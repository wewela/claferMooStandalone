# ClaferMoo

Performs multi-objective optimization over clafer models, which can encode attributed feature models.

## Dependencies

* Clafer Translator binary has to be in your path
* ** You can download a clafer binary for mac/linux/windows from https://github.com/gsdlab/claferig/downloads. Copy the file called clafer (or clafer.exe) into your path. 
* Python 2.x > 2.7  
* Java 32-bits as we use JNI 3	2-bits.

## Install

* git clone git@github.com:gsdlab/claferMooStandalone.git
   
## Getting Started
 * After installing:
 * cd claferMooStandalone
 * cd 2012-models-clafermultiobjective-data-generator/spl_datagenerator
 * python IntegratedFeatureModelOptimizer.py  ../dataset/linkedlistsplc2011.cfr 
 * This should provide the following output:
 *	** Running  alloy on generated als.
 *	** Finished Running alloy on generated als.
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

## Troubleshooting

* Clafer is not in your path *

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


* ** Solution 
Download clafer-tools from https://github.com/gsdlab/claferig/downloads. and copy the file called clafer (or clafer.exe) into your path. 

* You are running (e.g calling)  IntegratedFeatureModelOptimizer.py from a directory other than claferMooStandalone/2012-models-clafermultiobjective-data-generator/spl_datagenerator  *
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

* ** Solution
As relative paths to the tools directory are used, you must cd to claferMooStandalone/2012-models-clafermultiobjective-data-generator/spl_datagenerator and only from there call python IntegratedFeatureModelOptimizer.py 

* Your machine is unable to start a java virtual machine with heap size of min 512M and max 4096M *
Running  alloy on generated als.
Traceback (most recent call last):
  File "IntegratedFeatureModelOptimizer.py", line 91, in <module>
    execute_main()
  File "IntegratedFeatureModelOptimizer.py", line 57, in execute_main
    subprocess.check_output(["java", '-Xss3m', '-Xms80244m', '-Xmx16096m',  '-jar','../tools/multiobjective_alloy_cmd.jar', (filename[:-4] + ".als")])
  File "/System/Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/subprocess.py", line 537, in check_output
    raise CalledProcessError(retcode, cmd, output=output)
subprocess.CalledProcessError: Command '['java', '-Xss3m', '-Xms512m', '-Xmx4096m', '-jar', '../tools/multiobjective_alloy_cmd.jar', '../dataset/linkedlistsplc2011_desugared.als']' returned non-zero exit status 1

* ** Solution
Change in IntegratedFeatureModelOptimizer.py the paramaters ('-Xms512m' and '-Xmx4096m') passed to the java VM in line "    subprocess.check_output(["java", '-Xss3m', '-Xms512m', '-Xmx4096m',  '-jar','../tools/multiobjective_alloy_cmd.jar', (filename[:-4] + ".als")])"



## Dataset used in NFPinDSML12 (Fourth International Workshop on Non-functional System Properties in Domain Specific Modeling Languages)

It is located in directories claferMooStandalone /2012-models-clafermultiobjective-data-generator/satisfiable_partial_configurations_dataset and /2012-models-clafermultiobjective-data-generator/non_configured_dataset .