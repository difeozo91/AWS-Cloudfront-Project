# AWS Content Delivery Using CloudFront and S3

## Project Overview

This project demonstrates how to distribute static website content using Amazon CloudFront and Amazon S3.

The objective was to understand Content Delivery Networks (CDNs), origin storage, caching, HTTPS communication, and secure access between AWS services.

Amazon S3 stores the website files, while Amazon CloudFront delivers the content to website visitors through its distribution network.

Origin Access Control (OAC) was configured to prevent direct public access to the S3 bucket.

## Project Objectives

- Understand Content Delivery Networks.
- Configure Amazon CloudFront.
- Use Amazon S3 as an origin.
- Configure Origin Access Control (OAC).
- Restrict direct public access to S3 objects.
- Configure HTTPS delivery.
- Understand CloudFront caching.
- Test content delivery and origin security.

## AWS Services and Technologies

| Service | Purpose |
|---|---|
| Amazon CloudFront | Global content delivery |
| Amazon S3 | Website object storage |
| Origin Access Control | Authenticated access to S3 |
| AWS IAM concepts | Service-to-service permissions |
| HTTPS | Encrypted website communication |

## Architecture

Website visitors access content through Amazon CloudFront.

CloudFront retrieves website files from a private S3 bucket using Origin Access Control.

### Request Flow

1. Visitor requests the website through CloudFront.
2. CloudFront checks its cache.
3. If the content is not cached, CloudFront sends an authenticated request to S3.
4. S3 evaluates the bucket policy.
5. S3 returns the requested object to CloudFront.
6. CloudFront delivers the content to the visitor.

## Security Configuration

- S3 Block Public Access remained enabled.
- Origin Access Control was configured.
- CloudFront was granted read access through an S3 bucket policy.
- Access was restricted to the designated CloudFront distribution.
- HTTPS redirection was enabled for website visitors.
- No public write or delete permissions were granted.

## Caching

CloudFront caches website objects at its edge locations.

This reduces repeated requests to the S3 origin and can improve website delivery performance.

The `X-Cache` response header was used to investigate cache hits and misses.

## Testing

The following tests were performed:

- CloudFront website accessibility.
- HTTPS delivery.
- HTTP-to-HTTPS redirection.
- Direct S3 access restriction.
- Website content retrieval.
- CloudFront cache response headers.

## Cost Considerations

The project was designed around the CloudFront $0/month Free plan.

S3 usage may still incur applicable charges. Resources were removed after testing.

## Lessons Learned

- How a CDN distributes content.
- The difference between an origin and an edge location.
- How CloudFront communicates with S3.
- How OAC authenticates requests.
- How resource-based policies restrict access.
- How HTTPS protects website delivery.
- How caching reduces repeated origin requests.

1. What problem does CloudFront solve?

CloudFront speeds up content delivery by distributing website content through a global network of edge locations, reducing latency for users.

2. What is the difference between an origin and an edge location?
- Origin: The original location where content is stored, such as an S3 bucket.
- Edge location: A CloudFront location that caches and delivers content closer to users.
3. How does CloudFront communicate with S3?

CloudFront sends requests to the S3 origin. S3 checks the bucket policy and, if authorized, returns the requested objects to CloudFront.

4. Why do we use OAC?

Origin Access Control allows CloudFront to securely access a private S3 bucket without making the bucket publicly accessible.

5. What is the difference between OAC and a public bucket policy?
- OAC: Restricts access to authenticated CloudFront requests.
- Public bucket policy: Allows anyone to access objects if public access restrictions permit it.
6. What is caching?

Caching is temporarily storing website content so it can be delivered faster without repeatedly retrieving it from the original source.

7. What is the difference between a cache hit and cache miss?
- Cache hit: CloudFront already has the requested content cached and serves it.
- Cache miss: CloudFront retrieves the content from the origin, such as S3.
8. Why does CloudFront support HTTPS while the direct S3 website endpoint does not?

CloudFront supports HTTPS through its SSL/TLS certificates and distribution domain. The direct S3 static website endpoint only supports HTTP.

## Project Status

Completed – AWS CloudFront and S3 Content Delivery Lab.





