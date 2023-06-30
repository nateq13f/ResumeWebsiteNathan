# ResumeWebsiteNathan
Resume website with CI/CD from github to s3

## Deployment

- Codepipeline from Github to s3 on the Push action 


### SECURITY

FIXED -- had to add the KMS key in Codepipeline for object uploading, also had to add Codepipeline to the KMS policy so KMS authorizes that service to use it.

When using SSE-KMS, the incoming requests MUST be signed with sig-v4, however to do this the easy way is through CloudFront OAC (Origin Access Control). Enabling OAC, you can simply check the box to have every request signed and it will automatically sign it with sig-v4 instead of having to manually create a Lamdba@Edge origin request function where you code the signer.

Also, with OAC, you can lock the bucket down to have access only though CloudFront.