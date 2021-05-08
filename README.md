# CDK Project to create Google SSO Cognito 

## Resources to be created

* Cognito Userpool
  * App Clinets
    * web
    * web for local dev: may be unnecessary
    * native: may be unnecessary
  * Custom Domain
  * Google Idp
* SSM Parameters
  * Several Ids for JavaScript Clinets Login
  * Iam Role arn for IdPool authenticated / unauthenticated users.

[diagram by cfn-dia](https://diagram.figmentresearch.com/auth2)

## Purpose

Authentication for microservices

### How to use the resources this CDK project creates

Example Typescript code.

#### Example

cdk.json
```json
"iamrolearn_ssmparamname": "/auth2/cognito/idpool/auth/iam/role/arn",
```

CDK stack 
```Typescript
const iamrolearn_ssmparamname = this.node.tryGetContext('iamrolearn_ssmparamname')
const iamrolearn = ssm.StringParameter.valueFromLookup(this, iamrolearn_ssmparamname)
const iamrole = iam.Role.fromRoleArn(this, 'Role', iamrolearn)
```

## Commands

* `npm install`
* `cdk deploy`
* `aws ssm get-parameters-by-path --path xxxxx --recursive`
* `npm run diagram`
* `npm run save-context`

## Parameters

These parameters are defined in cdk.json 

* domain name
* SSM Parameter name
* Output name

