# serverspec-on-appveyor [![Build status](https://ci.appveyor.com/api/projects/status/f73dgnq8823g477a?svg=true)](https://ci.appveyor.com/project/StefanScherer/serverspec-on-appveyor)
Run serverspec tests on AppVeyor

Helper repo for discussion in http://help.appveyor.com/discussions/problems/5170-progresspreference-not-works-always-shown-preparing-modules-for-first-use-in-stderr to investigate Ruby + serverspec test issues on AppVeyor.

## Workaround

Adding `-NoProfile` seems to fix the issue. Filed a PR https://github.com/mizzy/specinfra/pull/584
```
(Get-Content vendor\bundle\ruby\2.2.0\gems\specinfra-2.63.1\lib\specinfra\backend\cmd.rb) | Foreach-Object {$_ -replace '-encodedCommand', '-NoProfile -encodedCommand'} | Out-File -Encoding ascii vendor\bundle\ruby\2.2.0\gems\specinfra-2.63.1\lib\specinfra\backend\cmd.rb
```
