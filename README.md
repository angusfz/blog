<!-- TOC -->

- [Notes](#notes)
	- [HTTP](#http)
		- [Cache relation header](#cache-relation-header)
	- [Git](#git)
	- [Misc](#misc)
- [Studying](#studying)
	- [AWS](#aws)
		- [Cloudfront](#cloudfront)

<!-- /TOC -->

## Notes

### HTTP

#### Cache relation header

- [Expires](https://tools.ietf.org/html/rfc7234#section-5.3)

```text
Expires = "Expires" ":" HTTP-date
Expires: Thu, 01 Dec 1994 16:00:00 GMT
```

if [ cache-control: max-age=N && Expires ], expires should be ignored and using $N

- [Cache-control](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.9)

Reference: 

[Header Field Definitions](https://tools.ietf.org/html/rfc7234#section-5.2.2)

### Git

[Semantic Commit Messages](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716)

- chore: (updating grunt tasks etc; no production code change)
- docs: (changes to the documentation)
- feat: (new feature for the user, not a new feature for build script)
- fix: (bug fix for the user, not a fix to a build script)
- refactor: (refactoring production code, eg. renaming a variable)
- style: (formatting, missing semi colons, etc; no production code change)
- test: (adding missing tests, refactoring tests; no production code change)

[Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/#summary)

### Misc

[Decrypting SSL/TLS traffic with Wireshark](https://resources.infosecinstitute.com/decrypting-ssl-tls-traffic-with-wireshark/)

## Studying

### AWS

[Building serverless applications with the AWS CDK - and testing them locally](https://sanderknape.com/2019/05/building-serverless-applications-aws-cdk/#displaying-cloudformation-changes)

#### Cloudfront

[This is How I Reduced My CloudFront Bills by 80%](https://medium.com/faun/this-is-how-i-reduced-my-cloudfront-bills-by-80-a7b0dfb24128)

<https://github.com/awsdocs/amazon-cloudfront-developer-guide>