# AFE-TSER
Automatic Feature Engineering for Time Series Extrinsic Regression

Examples :

`python3.9 evaluator.py -n 1000 -t regression -e RidgeCV -kw '{}' -r add -b Covid3Month -l catch22 -s csv --scale`

extract features using Catch22 library for Covid3month data set, add obtained features to original series representation, uses RidgeCV as end regressor with pre-scaling features. Generated features data are saved in csv files.

`python3.9 evaluator.py -n 1000 -t regression -e XGBRegressor -kw '{}' -r add -b Covid3Month -l catch22 -p --scale`

if features have been generated and saved in a previous experiment, `-p` allows pre-loading without re-generating features.

`python3.9 evaluator.py -n 1000 -t regression -e DecisionTreeRegressor -kw '{}' -s csv -p --scale`

not using `-b` for a specific data set, nor `-l` for a specific library implies launching experiments for all data sets and libraries (from utils.py)

General parametrization of the script : 
```
usage: evaluator.py [-h] [-d DATAPATH] [-f SAVEPATH] [-n MAX_FEATURES] [-e ESTIMATOR] [-kw KWARGS] [-t TASK]
                    [-s SAVE] [-p | --preload | --no-preload] [-sc | --scale | --no-scale] [-v VERBOSITY]
                    [-j N_JOBS] [-np NON_PYTHON] [-r RAW] [-b BASE] [-l LIBRARY]

optional arguments:
  -h, --help            show this help message and exit
  -d DATAPATH, --datapath DATAPATH
                        Path to data, .ts files
  -f SAVEPATH, --savepath SAVEPATH
                        Path in which features files are saved / from which are load
  -n MAX_FEATURES, --max_features MAX_FEATURES
                        Maximum number of features to extract when infinite feature space
  -e ESTIMATOR, --estimator ESTIMATOR
                        sklearn compatible estimator to perform desired task
  -kw KWARGS, --kwargs KWARGS
                        Keywords arguments for your estimator
  -t TASK, --task TASK  Task to perform : classification or regression
  -s SAVE, --save SAVE  Whether to save features matrices or not in data dir, if so specify format (npz or csv)
  -p, --preload, --no-preload
                        Whether you want to preload features from data path (default: False)
  -sc, --scale, --no-scale
                        Whether to apply standard scaling to features matrix before estimator (default: False)
  -v VERBOSITY, --verbosity VERBOSITY
                        Level of displayed information from 0 to 2
  -j N_JOBS, --n_jobs N_JOBS
                        Number of jobs tu run in parrallel for compatible libraries
  -np NON_PYTHON, --non_python NON_PYTHON
                        Whether to add non-python libraries
  -r RAW, --raw RAW     Whether to use raw series data (only), features (None) or add raw + features (add)
  -b BASE, --base BASE  String name of the data base or all datasets from repository (default)
  -l LIBRARY, --library LIBRARY
                        String name of the feature library to be used or all pre-defined libraries (default)

```
