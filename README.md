# How_To_Install_DeepChem_And_Pymol_In_Conda_Virtual_Environment

## 1. Go to [Anaconda.com](https://www.anaconda.com/) and install anaconda individual edition
![figure_1](https://github.com/NoriKaneshige/How_To_Install_DeepChem_And_Pymol_In_Conda_Virtual_Environment/blob/master/anaconda.png)
## 2. Check if anaconda is successfully installed or not by typing "which conda" and "conda -h"
```
(base) Koitaro@v-foreseer-local-mitc ~ % which conda
conda () {
	if [ "$#" -lt 1 ]
	then
		"$CONDA_EXE" $_CE_M $_CE_CONDA
	else
		\local cmd="$1"
		shift
		case "$cmd" in
			(activate | deactivate) __conda_activate "$cmd" "$@" ;;
			(install | update | upgrade | remove | uninstall) CONDA_INTERNAL_OLDPATH="${PATH}" 
				__add_sys_prefix_to_path
				"$CONDA_EXE" $_CE_M $_CE_CONDA "$cmd" "$@"
				\local t1=$?
				PATH="${CONDA_INTERNAL_OLDPATH}" 
				if [ $t1 = 0 ]
				then
					__conda_reactivate
				else
					return $t1
				fi ;;
			(*) CONDA_INTERNAL_OLDPATH="${PATH}" 
				__add_sys_prefix_to_path
				"$CONDA_EXE" $_CE_M $_CE_CONDA "$cmd" "$@"
				\local t1=$?
				PATH="${CONDA_INTERNAL_OLDPATH}" 
				return $t1 ;;
		esac
	fi
}
(base) Koitaro@v-foreseer-local-mitc ~ % conda -h
usage: conda [-h] [-V] command ...

conda is a tool for managing and deploying applications, environments and packages.

Options:

positional arguments:
  command
    clean        Remove unused packages and caches.
    config       Modify configuration values in .condarc. This is modeled
                 after the git config command. Writes to the user .condarc
                 file (/Users/Koitaro/.condarc) by default.
    create       Create a new conda environment from a list of specified
                 packages.
    help         Displays a list of available conda commands and their help
                 strings.
    info         Display information about current conda install.
    init         Initialize conda for shell interaction. [Experimental]
    install      Installs a list of packages into a specified conda
                 environment.
    list         List linked packages in a conda environment.
    package      Low-level conda package utility. (EXPERIMENTAL)
    remove       Remove a list of packages from a specified conda environment.
    uninstall    Alias for conda remove.
    run          Run an executable in a conda environment. [Experimental]
    search       Search for packages and display associated information. The
                 input is a MatchSpec, a query language for conda packages.
                 See examples below.
    update       Updates conda packages to the latest compatible version.
    upgrade      Alias for conda update.

optional arguments:
  -h, --help     Show this help message and exit.
  -V, --version  Show the conda version number and exit.

conda commands available from other packages:
  build
  convert
  debug
  develop
  env
  index
  inspect
  metapackage
  render
  server
  skeleton
  verify
```
## 3. Create an environment by "conda create", you can name it
```
(base) Koitaro@v-foreseer-local-mitc ~ % conda create -n biophysics_435
Collecting package metadata (current_repodata.json): done
Solving environment: done


==> WARNING: A newer version of conda exists. <==
  current version: 4.8.3
  latest version: 4.8.4

Please update conda by running

    $ conda update -n base -c defaults conda



## Package Plan ##

  environment location: /Users/Koitaro/opt/anaconda3/envs/biophysics_435



Proceed ([y]/n)? y

Preparing transaction: done
Verifying transaction: done
Executing transaction: done
#
# To activate this environment, use
#
#     $ conda activate biophysics_435
#
# To deactivate an active environment, use
#
#     $ conda deactivate
```

## 4. Activate the environment, so you can enter the environment
```
(base) Koitaro@v-foreseer-local-mitc ~ % conda activate biophysics_435
```
## 5. Install DeepChem and Tensorflow in the created environment, biophysics_435
```
(biophysics_435) Koitaro@v-foreseer-local-mitc ~ % conda install -c conda-forge rdkit deepchem==2.3.0

(biophysics_435) Koitaro@v-foreseer-local-mitc ~ % pip install tensorflow==1.14

```
## 6. Check if DeepChem is successfully installed or not by opening python shell and importing deepchem module
```
(biophysics_435) Koitaro@v-foreseer-local-mitc ~ % python
Python 3.7.8 | packaged by conda-forge | (default, Jul 31 2020, 02:37:09) 
[Clang 10.0.1 ] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import deepchem
```
## 7. Install Pymol
```
(biophysics_435) Koitaro@v-foreseer-local-mitc ~ % conda install -c schrodinger pymol-bundle -n mypymol

EnvironmentLocationNotFound: Not a conda environment: /Users/Koitaro/opt/anaconda3/envs/mypymol

(biophysics_435) Koitaro@v-foreseer-local-mitc ~ % conda install -c schrodinger pymol-bundle -n mypymol -m

```
## 8. Check if Pymol is successfully installed or not. Make sure you enter the environment for Pymol, Ctr + C to quit Pymol
```
(biophysics_435) Koitaro@v-foreseer-local-mitc ~ % pymol
zsh: command not found: pymol
(biophysics_435) Koitaro@v-foreseer-local-mitc ~ % conda activate mypymol
(mypymol) Koitaro@v-foreseer-local-mitc ~ % pymol

```
## 9. Deactivate the environments
```
(mypymol) Koitaro@v-foreseer-local-mitc ~ % conda deactivate
(biophysics_435) Koitaro@v-foreseer-local-mitc ~ % conda deactivate
(base) Koitaro@v-foreseer-local-mitc ~ % 

```

