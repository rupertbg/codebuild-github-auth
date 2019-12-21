# Example: CodeBuild Credentials for Github in Cloudformation
`codebuild-auth.yml` is an example of how to deploy an [Access Token for Github](https://docs.aws.amazon.com/codebuild/latest/userguide/sample-access-tokens.html) so that CodeBuild can work with features like having [Github as a direct webhook source](https://docs.aws.amazon.com/codebuild/latest/userguide/sample-github-pull-request.html).

This is particularly handy if you don't want to have to use the manual Console-based method to configure your credentials. There is also the added benefit of having your Personal Access Token stored securely in Secrets Manager.

`github-secret.yml` is an example of how to deploy the Secret into Secrets Manager.

## Usage
1. Deploy your Personal Access Token from Github into Secrets Manager per `github-secret.yml`. Your Personal Access Token gets deployed as a blank string.
2. You will need to manually navigate to the Secret in Secrets Manager and add your Personal Access Token into the Secret. The irony being the reason why we use Secrets Manager is the same reason why there's no other way to do this!
3. Deploy your CodeBuild Credentials via `codebuild-auth.yml`. The Personal Access Token is deployed securely using a [Dynamic Reference to the Secret](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/dynamic-references.html).


## TODO
  - Add a rotation lambda
