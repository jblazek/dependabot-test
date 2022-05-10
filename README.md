# Dependabot PR Open Issue

This repo contains Docker files to reproduce an issue with Dependabot.

## Issue

Files saved with UTF-8 BOM encoding do not trigger Dependabot PRs.

* Dockerfile1 has UTF-8 encoding and triggers scanning for update.
* Dockerfile2 has UTF-8  BOM encoding and no image is recognized.

## Example Logs

### Relevant Dependabot Log

#### Dockerfile1

```text
updater | INFO <job_362848288> Starting job processing
updater | INFO <job_362848288> Starting update job for jblazek/dependabot-test
updater | INFO <job_362848288> Checking if dotnet/aspnet 5.0.7-alpine3.13 needs updating

...other log entries checking dependency version...

updater | INFO <job_362848288> Finished job processing
```

#### Dockerfile2

```text
updater | INFO <job_362848288> Starting job processing

...other log entries, no dependency is detected...

updater | INFO <job_362848288> Finished job processing
```

### Full Dependabot Log

```text
  proxy | time="2022-05-10T02:08:02Z" level=info msg="proxy starting" commit=d0e8fc9c52e08bf359a8a4cff6deb91b01c23136
  proxy | 2022/05/10 02:08:02 Listening (:1080)
updater | 2022-05-10T02:08:02.831540828 [anonymous-instance:main:WARN:src/firecracker/src/main.rs:370] You are using a deprecated parameter: --seccomp-level 2, that will be removed in a future version.
updater | 2022-05-10T02:08:02.852910837 [362848288:main:WARN:src/devices/src/legacy/serial.rs:432] Detached the serial input due to peer close/error.
updater | time="2022-05-10T02:08:04Z" level=info msg="guest starting" commit=d54c1f07420d2f98b700854f969f92bffb6a9ded
updater | time="2022-05-10T02:08:04Z" level=info msg="starting job..." fetcher_timeout=5m0s job_id=362848288 updater_timeout=45m0s updater_version=0.185.0-37e671a530f3bce9868cd80691e6defeff4d0306
updater | I, [2022-05-10T02:08:05.763367 #7]  INFO -- sentry: ** [Raven] Raven 3.1.2 ready to catch errors
updater | warning: parser/current is loading parser/ruby27, which recognizes2.7.6-compliant syntax, but you are running 2.7.5.
updater | Please see https://github.com/whitequark/parser#compatibility-with-ruby-mri.
updater | INFO <job_362848288> Starting job processing
  proxy | 2022/05/10 02:08:07 [002] GET https://api.github.com:443/repos/jblazek/dependabot-test
  proxy | 2022/05/10 02:08:07 [002] * authenticating github api request
  proxy | 2022/05/10 02:08:07 [002] 200 https://api.github.com:443/repos/jblazek/dependabot-test
  proxy | 2022/05/10 02:08:07 [004] GET https://api.github.com:443/repos/jblazek/dependabot-test/git/refs/heads/main
  proxy | 2022/05/10 02:08:07 [004] * authenticating github api request
  proxy | 2022/05/10 02:08:08 [004] 200 https://api.github.com:443/repos/jblazek/dependabot-test/git/refs/heads/main
  proxy | 2022/05/10 02:08:08 [006] GET https://api.github.com:443/repos/jblazek/dependabot-test/contents/?ref=eef3df9d45488328fecc3d2f9cb7f93a8521f526
  proxy | 2022/05/10 02:08:08 [006] * authenticating github api request
  proxy | 2022/05/10 02:08:08 [006] 200 https://api.github.com:443/repos/jblazek/dependabot-test/contents/?ref=eef3df9d45488328fecc3d2f9cb7f93a8521f526
  proxy | 2022/05/10 02:08:08 [008] GET https://api.github.com:443/repos/jblazek/dependabot-test/contents/Dockerfile1?ref=eef3df9d45488328fecc3d2f9cb7f93a8521f526
  proxy | 2022/05/10 02:08:08 [008] * authenticating github api request
  proxy | 2022/05/10 02:08:08 [008] 200 https://api.github.com:443/repos/jblazek/dependabot-test/contents/Dockerfile1?ref=eef3df9d45488328fecc3d2f9cb7f93a8521f526
  proxy | 2022/05/10 02:08:08 [010] GET https://api.github.com:443/repos/jblazek/dependabot-test/contents/Dockerfile2?ref=eef3df9d45488328fecc3d2f9cb7f93a8521f526
  proxy | 2022/05/10 02:08:08 [010] * authenticating github api request
  proxy | 2022/05/10 02:08:08 [010] 200 https://api.github.com:443/repos/jblazek/dependabot-test/contents/Dockerfile2?ref=eef3df9d45488328fecc3d2f9cb7f93a8521f526
updater | INFO <job_362848288> Finished job processing
updater | time="2022-05-10T02:08:08Z" level=info msg="task complete" container_id=job-362848288-file-fetcher exit_code=0 job_id=362848288 step=fetcher
updater | I, [2022-05-10T02:08:09.337430 #8]  INFO -- sentry: ** [Raven] Raven 3.1.2 ready to catch errors
updater | warning: parser/current is loading parser/ruby27, which recognizes2.7.6-compliant syntax, but you are running 2.7.5.
updater | Please see https://github.com/whitequark/parser#compatibility-with-ruby-mri.
updater | INFO <job_362848288> Starting job processing
updater | INFO <job_362848288> Starting update job for jblazek/dependabot-test
updater | INFO <job_362848288> Checking if dotnet/aspnet 5.0.7-alpine3.13 needs updating
  proxy | 2022/05/10 02:08:11 [014] GET https://mcr.microsoft.com:443/v2/dotnet/aspnet/tags/list
  proxy | 2022/05/10 02:08:11 [014] 200 https://mcr.microsoft.com:443/v2/dotnet/aspnet/tags/list
  proxy | 2022/05/10 02:08:12 [016] HEAD https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/latest
  proxy | 2022/05/10 02:08:12 [016] 200 https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/latest
  proxy | 2022/05/10 02:08:12 [018] HEAD https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/7.0
  proxy | 2022/05/10 02:08:12 [018] 200 https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/7.0
  proxy | 2022/05/10 02:08:12 [020] HEAD https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/6.0.4
  proxy | 2022/05/10 02:08:12 [020] 200 https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/6.0.4
updater | INFO <job_362848288> Latest version is 6.0-alpine3.13
  proxy | 2022/05/10 02:08:12 [022] HEAD https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/5.0.7-alpine3.13
  proxy | 2022/05/10 02:08:12 [022] 200 https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/5.0.7-alpine3.13
  proxy | 2022/05/10 02:08:12 [024] HEAD https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/6.0-alpine3.13
  proxy | 2022/05/10 02:08:12 [024] 200 https://mcr.microsoft.com:443/v2/dotnet/aspnet/manifests/6.0-alpine3.13
updater | INFO <job_362848288> Pull request already exists for dotnet/aspnet with latest version 6.0-alpine3.13
updater | INFO <job_362848288> Finished job processing
updater | time="2022-05-10T02:08:13Z" level=info msg="task complete" container_id=job-362848288-updater exit_code=0 job_id=362848288 step=updater
```
