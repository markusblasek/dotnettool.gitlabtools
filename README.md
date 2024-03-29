[![NuGet Version](https://img.shields.io/nuget/v/GitLabTools.svg)](https://www.nuget.org/packages/GitLabTools/)
[![Github Action Status](https://img.shields.io/github/actions/workflow/status/markusblasek/dotnettool.gitlabtools/dotnet.yml)](https://github.com/markusblasek/dotnettool.gitlabtools/actions/workflows/dotnet.yml)
[![NuGet Downloads](https://img.shields.io/nuget/dt/GitLabTools.svg)](https://www.nuget.org/packages/GitLabTools/)
[![Coverage Status](https://coveralls.io/repos/github/markusblasek/dotnettool.gitlabtools/badge.svg?branch=main)](https://coveralls.io/github/markusblasek/dotnettool.gitlabtools?branch=main)

# GitLabTools

Tool to delete old pipelines from gitlab or read project/group information.

## License

The MIT License. See the [license](https://github.com/markusblasek/dotnettool.gitlabtools/blob/main/LICENSE) file for details.

## Install
`$ dotnet tool install --global gitlabtools --version 1.0.0`

### Install from local nuget
`$ dotnet tool install --global --add-source "#path_to_folder#" gitlabtools --version 1.0.0`

## Usage

Prerequisites:
  + GitLab personal access token with permission `api` - s. also [here](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)
  + URL to GitLab instance - e.g. `https://mygitlabinstance.com`

```bash
dotnet gitlabtools readProject --gitLabUrl https://mygitlabinstance.com --projectId 123456 --accessToken <PersonalAccessToken>
dotnet gitlabtools readGroup --gitLabUrl https://mygitlabinstance.com --groupId 654321 --accessToken <PersonalAccessToken>
dotnet gitlabtools deletePipelines --gitLabUrl https://mygitlabinstance.com --pipelinesToKeep 80 --projectId 123456  --accessToken <PersonalAccessToken>
dotnet gitlabtools deletePipelines --gitLabUrl https://mygitlabinstance.com --pipelinesToKeep 80 --projectId 123456  --accessToken <PersonalAccessToken> --dryRun
dotnet gitlabtools deletePipelines --gitLabUrl https://mygitlabinstance.com --pipelinesToKeep 80 --groupId 654321  --accessToken <PersonalAccessToken>
```

## Possible exit codes

| Exit code | Description |
|-----------|-----------------------------------------|
| 0         | ok                                      |
| 1         | Illegal arguments - e.g. url is invalid |
| 128       | Unexpected error occured                |

## Proxy

Proxy configuration is read from the environment variables `http_proxy`, `https_proxy` and `no_proxy`.
