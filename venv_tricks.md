Title: Bash helper functions for venv
Date: 2019-05-25
Category: Python
Tags: Python, bash, venv
Slug: bash-venv-functions
Author: L.J. Hanson
Summary: Useful helper functions for venv	

Working with python, I've always utilized virtualenvwrapper for creating and managing python setups for developing.  Now that more and more python work is moving over to Python 3, I wanted to start using more of the functionality it brings natively.  One of these is [Venv](https://docs.python.org/3/tutorial/venv.html) which is the native virtual environment system. 


One thing missing from the builtin system is some nice helper functions for use on the command line.  The following were copied from various[^1] sources[^2] but are posted below for reference as they should allow for the most common use cases.

~~~bash
# Python venv support functions
export VENV_HOME="$HOME/.venv"
[[ -d $VENV_HOME ]] || mkdir $VENV_HOME

venv() {
  source "$VENV_HOME/$1/bin/activate"
}

mkvenv() {
  python3 -m venv $VENV_HOME/$1
}

rmvenv() {
  rm -r $VENV_HOME/$1
}

lsvenv(){
    ls $VENV_HOME
}
~~~

[^1]: https://gist.github.com/dbtek/fb2ddccb18f0cf63a654ea2cc94c8f19
[^2]: https://stackoverflow.com/questions/45826517/python-venv-and-virtualenvwrapper-combined
