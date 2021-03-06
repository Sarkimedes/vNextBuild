A task to install and run PowerShell Pester based tests (Based on Pester 3.3.5)
The task takes two parameters 

- The root folder to look for test scripts with the naming convention  *.tests.ps1. Defaults to $(Build.SourcesDirectory)\*
- The results file name, defaults to $(Build.SourcesDirectory)\Test-Pester.XML

The Pester task does not in itself upload the test results, it just throws an error if tests fails. It relies on the standard test results upload task. 

So you also need to add the test results upload and set the following parameters

- Set it to look for nUnit format files
- It already defaults to the correct file name pattern.

IMPORTANT: As the Pester task will stop the build on an error you need to set the ‘Always run’ to make sure the results are published.

Once all this is added to your build you can see your Pester test results in the build summary