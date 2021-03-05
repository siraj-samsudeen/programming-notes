# Delete current versions of python and start with a clean slate

https://www.google.com/search?q=python+how+to+delete+and+restart+fresh

## How to uninstall mini conda? 
https://stackoverflow.com/questions/29596350/how-to-uninstall-mini-conda-python

Removed miniconda as per instructions given here

```bash
type python
> python is /Users/siraj/opt/miniconda3/bin/python
rm -rf /Users/siraj/opt/miniconda3
type python
> python is /usr/bin/python
python -V
> Python 2.7.16
```

Did `echo $PATH` and still found references to the python of conda. 
Then, opened .zshrc file. Conda has also set some paths in the .zshrc file at the end. Delete that block called `conda initialize`.
Now PATH does not contain any python paths. 

How to easily open files like .zprofile from Terminal? #flashcard 
Type `atom .zprofile` - this works beautifully

> This is not working properly - no matter what style of flashcard I use, this question is not being picked up. If I move it to the another section, it is picked up. 


## Right way to do a Python clean install on Mac
https://dev.to/aditya005/right-way-to-uninstall-clean-python-on-a-mac-4jfo
-   Mac comes with Python 2.7 which is at `/usr/bin/python`. This should NOT be touched
-   the python installations located in `/usr/local/bin` are often symbolic links and can be deleted.
-   List all the symbolic links to python by running ::  `$ ls -l /usr/local/bin/ | grep python*`
<!--ID: 1614380559236-->


- > I could not find any symbolic links in my Mac. Maybe, I deleted them earlier without realizing. 
- open `~/.bashrc` and `~/.bash_profile` and clean up all the references to python Framework path and only have  

```
export PATH='/usr/local/bin:/usr/local/sbin:/usr/bin:$PATH'
```

Q: How to see the contents of the `root` folder so that I can see files like .bash_profile?
A: In Terminal, go to root (`cd ~`). Then list all the files with `ls -a`. 

- Then, I opened the current folder in Atom with `atom .`. I found both .bash_profile and .zprofile. Deleted .bash_profile. 
- Then installed python using `$ brew install python3`

Q: How to update python3 in the future using homebrew?
A: brew upgrade python3
<!--ID: 1614380559245-->



When I ran `pip freeze`, I got an error pointing to some old version of pip that was in one of the python folders I deleted. So, ran ` ls -l /usr/local/bin/pip*` and found a few symbolic links to different versions of pip and deleted them all. 

Then, in order to just use pip rather than pip3, decided to create a symbolic link (thanks to what I have learnt from the [[Linux Command Line 5th Edition Notes]]).
The syntax for creating symbolic links is #flashcard `ln -s link item`. Counterintuitively, link comes first then the real item. 

```bash
ln -s /usr/local/bin/pip 
/usr/local/Cellar/python@3.9/3.9.1_1/bin/pip3
```

Then I ran `pip freeze` and the output is empty. Now it is time to set up a package manager for python. 

Then I came across this article, the first part of which covered the same contents above, but was much more friendly and clear. Then the rest discusses virtual environment and package manager for python
https://medium.com/faun/the-right-way-to-set-up-python-on-your-mac-e923ffe8cf8e

Now time to understsand the next item - [[Which package manager for python - pipenv or virtualenvwrapper or conda]]