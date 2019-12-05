---
title: Customizing content delivery at the Edge
cover_index: 2019/12/04/customizing-content-at-the-edge/index.jpg
tile_color: '#fea832'
date: 2019-12-04 15:09:07
tags:
---
{% asset_img banner.png "Customizing content delivery with Lambda@Edge" %}

Intercept request on viewer request and response and origin request and response.
Can be used to add headers, A/B testing and URL rewriting for example. Originless flows like redirecting.

Use https://observatory.mozilla.org/ to optimize website security.

## Lab 1 - Security
In modern web, many security features are implemented and enforced by the web browsers. The client-side security features are usually enabled and configured by HTTP response headers sent by a web server. However, a web server may not include all of the desired security headers in responses sent to your clients.
We will add several response headers to enable web browsers security features. For example, the Strict-Transport-Security response header protects your viewers from certain categories of the man-in-the-middle attacks, and the Content-Security-Policy header helps prevent cross-site scripting (XSS), clickjacking, and other code injection attacks resulting from execution of malicious content in the trusted web page context.
We will also configure your CloudFront distribution to always require HTTPS for communication between your viewers and CloudFront. All HTTP requests received by CloudFront will be redirected a corresponding HTTPS URL.
Lambda has a *Deploy to Lambda at edge* action, which is pretty handy. Lambda@Edge has support for Nodejs up until 10.x

## Lab 2 - Content Generation
With Lambda@Edge, you go beyond modifying HTTP requests and response that CloudFront receives from and sends to your viewers or your origin. Using your Lambda@Edge functions, you can generate content on the fly closest to your viewers without even going to an origin by returning a response from a Lambda@Edge function triggered by viewer-request or origin-request events.
By triggering lambda on origin-request, we can leave out the use of API gateway and trigger lambda straight from cloudfront.

## Lab 3 - Simple API
In order to make our simple website a little bit more interactive let's accept some feedback from the viewers and reflect it in the dynamically generated pages. In the previous lab, we made our home page list the cards according to the rating scores, but we have not yet implemented a way for our viewers to submit the "+1" feedback.
The downside of using lambda at edge instead of API Gateway is the manual checking for request method. You get GET, PUT, POST to the behaviour, CloudFront doesn't care for the method.

## Lab 4 - Pretty URLs
Pretty URLs are easy to read and remember. They also help with search engine ranking and allow your viewers to use the descriptive links in social media.
There are two common ways to serve content with pretty URLs:
- Redirect from semantic URLs similar to (b) to the URLs similar to (a) accepted by the origin
- Rewrite semantic URLs similar to (b) to URLs similar to (a) accepted by the origin. This can be done either by the origin itself or by an intermediate proxy. The URI rewrite approach has two advantages over the redirect:
- Faster content delivery as there is now need for an extra round-trip between the server and the client to handle the redirect 
- The semantic URLs stay in the address bar of the web browser

```
'use strict';

exports.handler = async (event) => {
    console.log('Event: ', JSON.stringify(event, null, 2));
    let request = event.Records[0].cf.request;

    // You can also use DynamoDB or S3 to store the redirect map
    // For demo purposes, we simply hardcode it here

    const redirects = {
        '/r/music':    '/card/bcbd2481',
        '/r/tree':     '/card/da8398f4',
        '/r/food':     '/card/e51c848c',
        '/r/computer': '/card/fe2f80a7',
        '/r/cat':      '/card/k9b430fc',
        '/r/beer':     '/card/vc7efa69',
    };

    if (redirects[request.uri]) {
        // generate 302 redirect response
        return {
            status: '302',
            statusDescription: 'Found',
            headers: {
                'location': [{ value: redirects[request.uri] }]
            }
        };
    }
    // pass through the request unchanged
    return request;
};
```

## Lab 5 - Customization
If you open the homepage of the CloudFront distribution, you set up in previous steps, on a mobile phone, you won't be able to see card descriptions and ratings as you can't hover over an HTML element without a pointer device on a mobile phone. If you try to hover, you may end up clicking it and landing on the detail page. While popping up elements look cool on a desktop, this is a poor viewer experience on a mobile device. We can fix this by keeping the hover effect only for desktop devices, while disaling it for mobile viewers who can just always see all descritpions and ratings without hovering over them.
You can serve customized content from an S3 bucket by changing the path prefix depending on the CloudFront device type headers like:
- CloudFront-Is-Mobile-Viewer
- CloudFront-Is-Desktop-Viewer

```
'use strict';

exports.handler = async (event) => {
    console.log('Event:', JSON.stringify(event, null, 2));
    const request = event.Records[0].cf.request;

    // Based on the value of the CloudFront-Is-Desktop-Viewer header,
    // we can re-write the URL to serve customized content.

    if (request.headers['cloudfront-is-desktop-viewer'] &&
        request.headers['cloudfront-is-desktop-viewer'][0].value !== 'true') {

        // it's not a desktop (it's  mobile, tablet or tv), use the mobile css
        request.uri = request.uri.replace(new RegExp('^/css/'),'/css/mobile/');
    }
    return request;
};
```

## Extra Challenges
Here is a few extra challanges for you if you feel up to it.

Why aliens that landed in, say, Japan are learning English? It would make sense for them to learn Japanese instead, perhaps using some authentic pictures and characters. With Lambda@Edge you can inspect CloudFront-Viewer-Country header and select a different S3 bucket (for example, in the ap-northeast-1 region) for CloudFront to fetch the images from using Content-Based Origin Selection feature. For more information, please refer to some public documentation:

https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-examples.html#lambda-examples-redirecting-examples
https://aws.amazon.com/blogs/networking-and-content-delivery/dynamically-route-viewer-requests-to-any-origin-using-lambdaedge/

Consider using Amazon DynamoDB Global tables. In the previous labs, we implemented Lambda@Edge functions in a way that they access a DynamoDB table in a single region, thus, introducing extra latency. This can be improved if DynamoDB table is replicated to multiple regions closer to where your viewers are. For more information, please refer to some public documentation:

https://aws.amazon.com/dynamodb/global-tables/
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GlobalTables.html

Sometimes, you may want to introduce a new change in your website to only a fraction of your viewers. You can do it with Lambda@Edge, for example, by rolling a dice and setting a cookie on the client side so that clients get consistent behavior, i.e. either variant A, or variant B, but not a mix of them.

https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-examples.html#lambda-examples-general-examples

Interested in exploring more use cases that Lambda@Edge supports? Check this out.

https://aws.amazon.com/blogs/networking-and-content-delivery/resizing-images-with-amazon-cloudfront-lambdaedge-aws-cdn-blog/
https://aws.amazon.com/blogs/networking-and-content-delivery/authorizationedge-how-to-use-lambdaedge-and-json-web-tokens-to-enhance-web-application-security/
https://aws.amazon.com/blogs/networking-and-content-delivery/category/networking-content-delivery/lambdaedge/