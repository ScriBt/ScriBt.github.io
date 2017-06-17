---
permalink: wiki/shellcheck.html
title: "ShellCheck"
---

![derpLife](https://cloud.githubusercontent.com/assets/14874906/26635154/736e11e8-4636-11e7-8581-d849519e09bd.png)

We are humans, and errors are bound to occur. To make sure there are no obvious/harmful errors, ScriBt is `shellcheck` ed on every Push/Pull Activity, automated by TravisCI.  

**Thanks to this work** - https://github.com/koalaman/shellcheck  
That this has been made possible. :pray:  

**TravisCI** page - https://travis-ci.org/ScriBt/ScriBt  
You can check this page to know the current status of ScriBt

**Status** : ![build &#124; passing](https://img.shields.io/badge/build-passing-brightgreen.svg)  OR  ![build &#124; failing](https://img.shields.io/badge/build-failing-red.svg)  

**We get the Build Status to be passing before shipping it (to master).**  

**Automation script** - https://github.com/ScriBt/ScriBt-Examples/blob/master/shellcheck_new.sh  

# Suppressed Flags

These warning flags by `shellcheck` have been suppressed with the reason for each flag shown below  
Any other Error/Warning flag pops up and the Build fails.

Information on these flags can be viewed in the ShellCheck Wiki, selecting the flag will open up a Wiki Page on that Flag

## ROM.sh    

[**SC2016**](https://github.com/koalaman/shellcheck/wiki/SC2016) -  for keeping the `$` literal in some commands 

[**SC2030**](https://github.com/koalaman/shellcheck/wiki/SC2030) -  Variables used in Subshell aren't used   
[**SC2031**](https://github.com/koalaman/shellcheck/wiki/SC2031) -  ^^  

[**SC2046**](https://github.com/koalaman/shellcheck/wiki/SC2046) -  In most of the cases, splitting is necessary  
[**SC2086**](https://github.com/koalaman/shellcheck/wiki/SC2086) -  ^^ e.g. Command and its parameters are to be split

<hr>

[**SC2119**](https://github.com/koalaman/shellcheck/wiki/SC2119) -  mah coding style  ¯\\\_(ツ)_/¯    
[**SC2120**](https://github.com/koalaman/shellcheck/wiki/SC2120) -  Same reason as above  

Common syntax for functions  

```
function <function_name>()
{
 ...
} # <function_name>
```

<hr>

[**SC2153**](https://github.com/koalaman/shellcheck/wiki/SC2153) -  Variables starting with "SB" are set by `shut_my_mouth`. They are not assigned the normal way  

**Normal Assignment** : `VAR="Value";`  
`shut_my_mouth` **Assignment** : `SB${SOMETHING} <- "Value"`  

<hr>

[**SC2154**](https://github.com/koalaman/shellcheck/wiki/SC2154) -  Same reason as SC2153  

[**SC2155**](https://github.com/koalaman/shellcheck/wiki/SC2155) -  Nothing required to do with return values  

## All files under src/

[**SC2034**](https://github.com/koalaman/shellcheck/wiki/SC2034) -  Variables are used in ROM.sh  

## upScriBt.sh

**NONE**  

## Common Flags

[**SC2164**](https://github.com/koalaman/shellcheck/wiki/SC2164) -  Variables are not fetched from the user. Therefore, no fallback is required

[**SC1090**](https://github.com/koalaman/shellcheck/wiki/SC1090) -  Most of the files which are `source`d are System Files  

[**SC1091**](https://github.com/koalaman/shellcheck/wiki/SC1091) - `source`'d files are system files  
