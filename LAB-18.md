![cf](https://i.imgur.com/7v5ASc8.png) Lab 18: Authorization
======

## Submission Instructions
* Continue from lab 17
* Submit on canvas a question and observation, how long you spent, and a link to your pull request

## Resources
* [express docs](http://expressjs.com/en/4x/api.html)
* [mongoosse guide](http://mongoosejs.com/docs/guide.html)
* [mongoosse api docs](http://mongoosejs.com/docs/api.html)
* [aws sdk](https://github.com/aws/aws-sdk-js)
* [aws sdk s3 docs](http://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/S3.html)
* [aws sdk mock docs](https://github.com/dwyl/aws-sdk-mock)

## Feature Tasks  
Create a third model that represents a file asset. The file should be stored on AWS S3, and metadata about the file should be stored in your mongo database.  
  
#### File Asset Model
Create a model with at least 4 properties that represents some type of file asset (BLOB) resource (image, audio, movie, 3d file). One of the models properites should account and should hold an Account _id. One of the properties should be `url` and should hold an AWS Location.

#### Server Endpoints
* `POST /<resouces-name>` 
  * pass a bearer authentication token in the request to authorize the creation of the resource
  * pass data as `multipart/form-data` in the body of a **POST** request to create a new resource
    * should include an attached file asset
  * on success respond with a 200 status code and an authentication token
  * on failure due to a bad request send a 400 status code
  * on failure due to bad token or lack of token respond with a 401 status code
* `GET /<resouces-name>/:id` 
  * pass a bearer authentication token in the request to authorize the creation of the resource
  * on success respond with a 200 status code and an authentication token
  * on failure due to a bad id send a 404 status code
  * on failure due to bad token or lack of token respond with a 401 status code
* `DELETE /<resouces-name>/:id` 
  * pass a bearer authentication token in the request to authorize the creation of the resource
  * on success respond with a 204 status code and an authentication token
  * on failure due to a bad id send a 404 status code
  * on failure due to bad token or lack of token respond with a 401 status code
  
## Tests
* Write 200, 400, and 401 tests for `POST /<resource-name>`
* Write 200, 404, and 401 tests for `GET /<resource-name>/:id`
* Write 204, 404, and 401 tests for `DELETE /<resource-name>/:id`

## Documentation
In the README.md write documention for starting your server and makeing requests to each endpoint it provides. The documentaion should describe how the server would respond to valid and invalid requests.
