# Upload an Image To S3
## Access it's EXIF data like Geolocation

### Setup
* Create an AWS bucket in S3
```
# using the aws cli (you will need to login with aws configure)
aws s3api create-bucket --bucket mynewbucket
```

* Store security information in a .env file in the projects
root directory. Make sure .env is set in the .gitignore file

* Store your unique AWS security and bucket information
in the .env file.

**Example**
```
#.env

AWS_BUCKET_NAME=mynewbucket
AWS_REGION=us-east-1
AWS_ACCESS_KEY_ID=myid123
AWS_SECRET_ACCESS_KEY=mykey123
```

* Update secrets.yaml to reference the env variables.

**Example**
```
#./secrets.yaml
development:
  secret_key_base: 8cdfddc7e3d3ed068d97ddcef1299505c25dd8138c934cee547a21ae72f70a54080e0beeb55c4245357f6d6250a0c84a4abaa942dadeddcc2a98a0b22387cba0
  aws_bucket_name: <%= ENV["AWS_BUCKET_NAME_STAGING"] %>
  aws_region: <%= ENV["AWS_REGION_STAGING"] %>
  aws_access_key_id: <%= ENV["AWS_ACCESS_KEY_ID_STAGING"] %>
  aws_secret_access_key: <%= ENV["AWS_SECRET_ACCESS_KEY_STAGING"] %>
test:
  secret_key_base: 93d039356f6ecec46214461d44f3bb63eceb0196a6a9c8d09f9061ec3df184441ff367670dcbec520a93e6d0d613cec8d44bfaa0d226eed3b7476dc8895e76f3
  aws_bucket_name: <%= ENV["AWS_BUCKET_NAME_STAGING"] %>
  aws_region: <%= ENV["AWS_REGION_STAGING"] %>
  aws_access_key_id: <%= ENV["AWS_ACCESS_KEY_ID_STAGING"] %>
  aws_secret_access_key: <%= ENV["AWS_SECRET_ACCESS_KEY_STAGING"] %>

# Do not keep production secrets in the repository,
# instead read values from the environment.
production:
  secret_key_base: <%= ENV["SECRET_KEY_BASE"] %>
  aws_bucket_name: <%= ENV["AWS_BUCKET_NAME_PRODUCTION"] %>
  aws_region: <%= ENV["AWS_REGION_PRODUCTION"] %>
  aws_access_key_id: <%= ENV["AWS_ACCESS_KEY_ID_PRODUCTION"] %>
  aws_secret_access_key: <%= ENV["AWS_SECRET_ACCESS_KEY_PRODUCTION"] %>

```

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


Please feel free to use a different markup language if you do not plan to run
<tt>rake doc:app</tt>.
