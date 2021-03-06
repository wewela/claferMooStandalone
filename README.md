ClaferMOO
=========

v0.3.5.20-01-2014

Performs multi-objective optimization over clafer models limited to the *attributed feature models with inheritance* subset of Clafer.

Contributors
------------

* [Rafael Olaechea](http://gsd.uwaterloo.ca/rolaechea), MSc. Candidate. Main developer.
* [Michał Antkiewicz](http://gsd.uwaterloo.ca/mantkiew), Research Engineer. Requirements, development, architecture, testing, technology transfer.
* [Alexandr Murashkin](http://gsd.uwaterloo.ca/amurashk), MSc. Candidate. Minor fixes.

Getting Clafer Tools
--------------------

Getting Clafer Tools
--------------------

Binary distributions of the release 0.3.5 of Clafer Tools for Windows, Mac, and Linux, 
can be downloaded from [Clafer Tools - Binary Distributions](http://http://gsd.uwaterloo.ca/clafer-tools-binary-distributions). 
Clafer Wiki requires Haskell Platform and MinGW to run on Windows. 

In case these binaries do not work on your particular machine configuration, the tools can be built from source code, as described below.

### Dependencies for running

* [Clafer](https://github.com/gsdlab/clafer) v0.3.4
* [Java Platform (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/index.html) v6+, 32bit
* [Python](http://www.python.org/download/) v2.7.*

## Installation

`git clone git@github.com:gsdlab/claferMooStandalone.git`
   
### Important: Branches must correspond

All related projects are following the *simultaneous release model*. 
The branch `master` contains releases, whereas the branch `develop` contains code under development. 
When building the tools, the branches should match.
Releases from branches 'master` are guaranteed to work well together.
Development versions from branches `develop` should work well together but this might not always be the case.

## Usage

After installing, execute:

 * `cd claferMooStandalone`
 * `cd 2012-models-clafermultiobjective-data-generator/spl_datagenerator`
 * `python IntegratedFeatureModelOptimizer.py  ../dataset/linkedlistsplc2011.cfr`

This should provide the following output:

```
 Running  alloy on generated als.
  Finished Running alloy on generated als.
		simpleConfig : LinkedList 
				AbstractElement : IMeasurable 
					ElementC : IMeasurable 
						footprint  =  0 
					footprint  =  -12 
				AbstractIterator : IMeasurable 
					ForwardIterator : IMeasurable 
						footprint  =  0 
					footprint  =  0 
				Base : IMeasurable 
					footprint  =  455 
				total_footprint  =  443 				
		simpleConfig : LinkedList 
			AbstractElement : IMeasurable 
				ElementB : IMeasurable 
					footprint  =  0 
				footprint  =  -12 
			AbstractIterator : IMeasurable 
				ForwardIterator : IMeasurable 
					footprint  =  0 
				footprint  =  0 
			Base : IMeasurable 
				footprint  =  455 
			total_footprint  =  443 
```

Troubleshooting
---------------

#### Clafer is not in your path

```
Traceback (most recent call last):
  File "IntegratedFeatureModelOptimizer.py", line 91, in <module>
    execute_main()
  File "IntegratedFeatureModelOptimizer.py", line 28, in execute_main
    stderr=subprocess.STDOUT)       
  File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/subprocess.py", line 530, in check_output
    process = Popen(stdout=PIPE, *popenargs, **kwargs)
  File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/subprocess.py", line 672, in __init__
    errread, errwrite)
  File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/subprocess.py", line 1202, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
```

  * Solution 

Download [clafer-tools](https://github.com/gsdlab/claferig/downloads) and copy the file called `clafer` or `clafer.exe` into your path. 

#### You are running (e.g calling)  `IntegratedFeatureModelOptimizer.py` from a directory other than `claferMooStandalone/2012-models-clafermultiobjective-data-generator/spl_datagenerator`

```
python claferMooStandalone/2012-models-clafermultiobjective-data-generator/spl_datagenerator/IntegratedFeatureModelOptimizer.py claferMooStandalone/2012-models-clafermultiobjective-data-generator/dataset/berkeleydbqualityjournal.cfr 
Running  alloy on generated als.
Unable to access jarfile ../tools/multiobjective_alloy_cmd.jar
Traceback (most recent call last):
  File "claferMooStandalone/2012-models-clafermultiobjective-data-generator/spl_datagenerator/IntegratedFeatureModelOptimizer.py", line 91, in <module>
    execute_main()
  File "claferMooStandalone/2012-models-clafermultiobjective-data-generator/spl_datagenerator/IntegratedFeatureModelOptimizer.py", line 57, in execute_main
    subprocess.check_output(["java", '-Xss3m', '-Xms512m', '-Xmx4096m',  '-jar','../tools/multiobjective_alloy_cmd.jar', (filename[:-4] + ".als")])
  File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/subprocess.py", line 537, in check_output
    raise CalledProcessError(retcode, cmd, output=output)
subprocess.CalledProcessError: Command '['java', '-Xss3m', '-Xms512m', '-Xmx4096m', '-jar', '../tools/multiobjective_alloy_cmd.jar', 'claferMooStandalone/2012-models-clafermultiobjective-data-generator/dataset/berkeleydbqualityjournal_desugared.als']' returned non-zero exit status 1
```

 * Solution

As relative paths to the tools directory are used, you must cd to `claferMooStandalone/2012-models-clafermultiobjective-data-generator/spl_datagenerator` and only from there call python `IntegratedFeatureModelOptimizer.py`. 

#### Your machine is unable to start a java virtual machine with heap size of min 512M and max 4096M

```
Running  alloy on generated als.
Invalid maximum heap size: -Xmx4096m
The specified size exceeds the maximum representable size.
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.
Traceback (most recent call last):
  File "IntegratedFeatureModelOptimizer.py", line 91, in <module>
    execute_main()
  File "IntegratedFeatureModelOptimizer.py", line 57, in execute_main
    subprocess.check_output(["java", '-Xss3m', '-Xms80244m', '-Xmx16096m',  '-jar','../tools/multiobjective_alloy_cmd.jar', (filename[:-4] + ".als")])
  File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/subprocess.py", line 537, in check_output
    raise CalledProcessError(retcode, cmd, output=output)
subprocess.CalledProcessError: Command '['java', '-Xss3m', '-Xms512m', '-Xmx4096m', '-jar', '../tools/multiobjective_alloy_cmd.jar', '../dataset/linkedlistsplc2011_desugared.als']' returned non-zero exit status 1
```

 * Solution

By adding the maxHeapSize argument to the end of your command you can change the maximum size of the allocated heap.
ex: `python IntegratedFeatureModelOptimizer.py  ../dataset/linkedlistsplc2011.cfr --maxHeapSize=1340`

> Hint: On Windows systems try `--maxHeapSize=1340`, which seems to be the maximum heap size that can be allocated.

## Dataset used in NFPinDSML12 

(Fourth International Workshop on Non-functional System Properties in Domain Specific Modeling Languages)

It is located in directories `claferMooStandalone/2012-models-clafermultiobjective-data-generator/satisfiable_partial_configurations_dataset` and `claferMooStandalone/2012-models-clafermultiobjective-data-generator/non_configured_dataset`.

Need help?
==========
* See [language's website](http://clafer.org) for news, technical reports and more
  * Check out a [Clafer tutorial](http://t3-necsis.cs.uwaterloo.ca:8091/Tutorial/Intro)
  * Try a live instance of [ClaferWiki](http://t3-necsis.cs.uwaterloo.ca:8091)
  * Try a live instance of [ClaferIDE](http://t3-necsis.cs.uwaterloo.ca:8094)
  * Try a live instance of [ClaferConfigurator](http://t3-necsis.cs.uwaterloo.ca:8093)
  * Try a live instance of [ClaferMooVisualizer](http://t3-necsis.cs.uwaterloo.ca:8092)
* Take a look at (incomplete) [Clafer wiki](https://github.com/gsdlab/clafer/wiki)
* Browse example models in the [test suite](https://github.com/gsdlab/clafer/tree/master/test/positive) and [MOO examples](https://github.com/gsdlab/clafer/tree/master/spl_configurator/dataset)
* Post questions, report bugs, suggest improvements [GSD Lab Bug Tracker](http://gsd.uwaterloo.ca:8888/questions/). Tag your entries with `clafermoo` (so that we know what they are related to) and with `rafael-olaechea` (so that Rafael gets a notification).
