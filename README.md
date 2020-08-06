# Introduction 
This is a Azure DevOps pipeline build agent test to see demonstrate the effects of GitvVersion-ing and tagging working on `ubuntu-latest` and not working on `windows-latest` agent.

The implementation is fairly vanilla.

See Reported GitHub issue : https://github.com/actions/virtual-environments/issues/1327

# Solution
https://github.com/actions/virtual-environments/issues/1327#issuecomment-666436552

Could you please add `$env:GIT_REDIRECT_STDERR = '2>&1'` command at the top of the pwsh task for Windows ?

```
$env:GIT_REDIRECT_STDERR = '2>&1'
git config user.name "Azure DevOps"
git config user.email "noreply@boq.com.au"
git tag $env:BuildNumber
git push --follow-tags origin $env:BuildNumber --verbose
```

fixed my the issue - magically :)
