issue so far

- not title 
  add one markdown cell on notebook "# my title" etc.
  BTW use

```{note}
 jupyter-book build --all imgnobk1/
```

- the toc has warning but it seems to generate; try add back here and delete in ImgPre (well, still have issue: "ImgPre.md:: WARNING: tableofcontents directive in document with no descendants [etoc.tableofcontents]")

```{note}
- seems if there is only one of the below Toc no warning now but if two document has it ... warning as above
```

- the website is not index.html and hence 404 but you can get to it

```{note}
https://kwccoin.github.io/ImginaryNo2/ImgIntro.html
```

- I am still not sure about the doc and \ things in [the public page](https://jupyterbook.org/en/stable/start/publish.html) 

```{note}
b. Choose root directory / if you’re building the book in it’s own repository. Choose /docs directory if you’re building documentation with jupyter-book.
```

or these message

```
$ ghp-import -n -p -f _build/html
Enumerating objects: 290, done.
Counting objects: 100% (290/290), done.
Delta compression using up to 16 threads
Compressing objects: 100% (137/137), done.
Writing objects: 100% (290/290), 3.22 MiB | 300.07 MiB/s, done.
Total 290 (delta 104), reused 290 (delta 104), pack-reused 0
remote: Resolving deltas: 100% (104/104), done.
remote: This repository moved. Please use the new location:
remote:   https://github.com/kwccoin/ImginaryNo2.git
remote: 
remote: Create a pull request for 'gh-pages' on GitHub by visiting:
remote:      https://github.com/kwccoin/ImginaryNo2/pull/new/gh-pages
remote: 
To https://github.com/kwccoin/imginaryno2
 * [new branch]      gh-pages -> gh-pages
$ 

```

- now you need to repeat this steps

```{note}
1. build
   - open under VSC imgno_book1 direcotry external terminal or

   - cd /Users/ngcchk/Documents/Github/gpd2-win-unity1/ipadred-rain/imgno_book1 
   - jupyter-book build --all imgnobk1/
     --- (note it assume you have imgnobk1/ as subdirectory)
   - jupyter-book build imgnobk1/ pdfhtml --- not working timeout
   - jupyter-book build imgnobk1/ pdflatex --- partially no Chinese

2. copy
   - cp -Rf imgnobk1/* ~/Documents/Github/imginaryno2/
   - cd ~/Documents/Github/imginaryno2/

   - ghp-import -n -p -f _build/html

   - git add ./*
   - git commit -m "3rd times said : need to do ghp-import -n -p -f _build/html"

3. publish
   - git push

    or use the script
   - cd /Users/ngcchk/Documents/Github/gpd2-win-unity1/ipadred-rain/imgno_book1 
   - sh update_imgnobk1_web.sh --- or sh up2.sh --- just _build

   - under windows shouls use ~/Documents/Github not user name
   -               try up2win.sh under git bash shell
   - still a lot missing ... python, p... pdflatex etc.
   - need to reinstall a lot of things first


```

- For books publishing

```{note}
 --- pip install pyppeteer
 cd /Users/ngcchk/Documents/Github/gpd2-win-unity1/ipadred-rain/imgno_book1  
 jupyter-book build imgnobk1/ --builder pdfhtml/
 --- [INFO] Starting Chromium download.
 --- [INFO] Chromium extracted to: /Users/ngcchk/Library/Application Support/pyppeteer/local-chromium/588429
```

- above does not work seems need to edit this or that

```{note}
see https://github.com/executablebooks/jupyter-book/issues/1732

This was with v13.0 of Jupyter Book and v1.0.3 of pyppeteer. I seemed to have fixed the problem by simply editing line 50 of pdf.py from

    await page.goto(f"file:///{html_file}", {"waitUntil": ["networkidle2"]})
to

    await page.goto(f"file:///{html_file}", {"timeout": 0, "waitUntil": ["networkidle2"]})
I'm not intimately familiar with the internal workings of Jupyter Book, or with pyppeteer so I'm not sure if this is a "good" fix or not. Would appreciate it if a core contributor can find the bandwidth to take a look at this.

```

- use latex (but does not by default support Traditional Chinese as usual; need to modify book.tex using the trick under TC, SC and Japanese song ...)

```{note}
 --- pip install pyppeteer
 cd /Users/ngcchk/Documents/Github/gpd2-win-unity1/ipadred-rain/imgno_book1  
 jupyter-book build imgnobk1/ --builder pdflatex
 --- problem with Chiense character though, edited latex
```

 I delete the TOC here but add back to ImgIntro.md

