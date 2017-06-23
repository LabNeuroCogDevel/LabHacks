# Programming
## Languages
* [`GNU R`](https://www.r-project.org/) is used by statisticians. Useful packages:
  * `dplyr` provides `%>%` for pipleline notation (`data %>% head %>% nrow` vs `nrow(head(data))`
  * `ggplot2` for grammer of graphs. high level plotting
  * `devtools` for developing packages. see [this tutorial](https://hilaryparker.com/2014/04/29/writing-an-r-package-from-scratch/)
  * [`LNCDR`](https://github.com/LabNeuroCogDevel/LNCDR) 

* shell (esp. `bash`) is the glue that binds everything together.
  * globing and pattern matching are extremely useful
     * `ls *201[67]*` 
     * `echo {a,b}{c,d}; mv data{,_$(date +%F)}` 
  * coreutils and pipes do the work of otherwise complicated scripts
     * `cut -f2 data.txt | sed 's/_.*//' | sort |uniq |wc -l`
     * `find . -newer 'prevfile.txt'`

* `Matlab` is proprietary and costly but nonetheless popular for number crunching and is the foundation for task presentation software [`Psychtoolbox`](http://psychtoolbox.org/). [`octave`](https://www.gnu.org/software/octave/) is the open source implementation (and has a builtin package manager [`forge`](https://octave.sourceforge.io/)). `python` and [`julia`](https://julialang.org/) are eating Matlab's lunch.

## Tools

### Text editors
* [`Rstudio`](https://www.rstudio.com/) is the most robust IDE for R.
* `vim` is available almost everywhere and will work on any server even without window forwarding. Learning vim is learning a grammar of text editing.


### Version Control
* `git` is the most popular version control system. `github` is the most popular (and free) git service provider.
  * [tutorial](http://www-cs-students.stanford.edu/~blynn/gitmagic/)
  * Matlab has built in menus for git
  * workflow (outside of any editor integration)
  ```bash
  git init # only once in the root folder of files to be tracked

  # add single file
  git add fileImEditing.R  # tell git to track file
  git commit -m 'desc. of changes made' # tell git about changes

  # AND/OR add all changes to already added files
  git commit -am 'totally changed analysis' # (a)uto commit all changes

  # OPTIONALLY
  git push # ptionally push those changes somewhere (e.g. github)
  ```

### Terminal multiplexers 
* `tmux` and `screen` are terminal multiplexers. They are useful creating a persistent session open in a terminal on a remote machine. Loose connection or close the terminal window? No problem; you're stuff will still be running and you can reconnect to it.

### Note taking
* [zim](http://zim-wiki.org/)

## Literate programming
* See [`org-babel`](http://orgmode.org/worg/org-contrib/babel/) for emacs
* [Rmarkdown](http://rmarkdown.rstudio.com/)

# Site Specific
## The UPMC Firewall
* Use [Box](box.com) Sync (supported by upmc)
* Use github or gitlab to get code in and out
### remote connect 
* https://accessprd.upmc.com/  + [MobaXterm](http://mobaxterm.mobatek.net/) in your `M:` dirve
* Triple hop ssh: 
  ```bash
  ssh unix.cssd.pitt.edu
  ssh web-server.mrctr.upmc.edu
  ssh rhea.wpic.upmc.edu
  ## optional pro mode, ssh server running at home, forward port 22 on router for server access
  # on rhea/work machine
  ssh -NMf homecomputer -L 19877:localhost:22
  # on home computer
  ssh labuser@localhost -p 198777
  ```
