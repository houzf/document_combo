Installation
=====================

Required Packages
----------------------
* Python 2.7.x
* numpy >=1.10
* scipy >= 0.16
* Cython >= 0.22.1
* mpi4py >= 2.0 (optional)

#. Copy the following contents to a text file named 'requirements.txt' ::

        ## To install these requirements, run
        ## pip install -U -r requirements.txt
        ## (the -U option also upgrades packages; from the second time on,
        ## just run
        ## pip install -r requirements.txt
        ##
        ## NOTE: before running the command above, you need to install a recent version
        ## of pip from the website, and then possibly install/upgrade setuptools using
        ## sudo pip install --upgrade setuptools
        ## numpy
        numpy >=1.10
        
        ## scipy
        scipy >= 0.16
        
        ##  
        Cython >= 0.22.1
        
        ## mpi4py 
        mpi4py >= 2.0 (optional)

#. Run the command  :: 

    > pip install -U -r requirements.txt

Install
----------------------
#. Download or clone the github repository, e.g. ::
        
   > git clone https://github.com/tsudalab/combo.git

#. Run setup.py install ::

   > cd combo
   > python setup.py install

Uninstall
----------------------
#. Delete all installed files, e.g. ::

   > python setup.py install --record file.txt
   > cat file.txt  | xargs rm -rvf


