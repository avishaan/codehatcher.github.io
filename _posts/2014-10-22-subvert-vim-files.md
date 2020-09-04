---
title: "Subvert with Vim Across Multiple files" 
excerpt: "f you aren't with it the following with work with built in vim :substitute"
categories:
  - Vim
tags:
  - Reference
  - Vim
toc: true
toc_sticky: true
---
1. Open one of the files you want to be included in your find and replace search.

2. Add that open file to your args list with `:argadd %` or `:arga %`

3. Repeat 1-2 above for all the files you want to include. You can do things like include all .js files with `:argadd *.js`

4. You can check that you have all the files by typing `:arg` You will get a list that looks something like this.

![See files in list](/assets/posts/migrated-codehatcher-blog/filesinargs_large.png)

5. Run your Subvert (or normal substitution) on the arglist with `:argdo`. For example, if you want to perform a Subvert use `:argdo %:Subvert/find/replace/gce` If you don't have Subvert you could do the built in substitute with `:argdo %:substitute/find/replace/gce` or more compactly, `:argdo %:s/find/replace/gce` 
The 'e' means you want to ignore errors. The 'c' means to confirm each.

![example replace](/assets/posts/migrated-codehatcher-blog/arg1step1ACTUALLY_large.png)

6. If you included 'c' then you will have to confirm each change which will present you with the following dialog. The confirmation would look something like this. 

![confirmation example](/assets/posts/migrated-codehatcher-blog/argdoconfirmfile_large.png)

similar to` :argdo`, check out using `:bufdo` and `:windo`