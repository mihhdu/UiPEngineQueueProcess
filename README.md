### UiPEngineQueueProcess ###
** Simple engine to pull and process a Transaction from an Orchestrator queue**

This engine contains code that will do the following:
1. Read a configuration file, by default located in Data\Config.xlsx and output as a dictionary named config
2. Calls ProcessLayer\InitAllApplications.xaml, where you should initialize apps
3. While there are items in the Queue, read a new Item and process it.
--3.1 Get Item from queue
--3.2 Execute Process - retry if you run into a AppEx
----3.2.1 Calls ProcessLayer\ProcessTransaction.xaml, where you should input data into your opened    apps
----3.2.2 Evaluate Process wb output
----3.2.3 Recover if wb failed with AppEx
------3.2.3.1 Call ProcessLayer\CloseAllApplications.xaml
------3.2.3.2 Call ProcessLayer\InitAllApplications.xaml
4. Call ProcessLayer\CloseAllApplications.xaml

### For New Project ###
To begin implementing take the following steps:

1. Check out the *Data\Config.xlsx* file and add/customize any required fields and values. Make sure you specify the queue name in the config.

2. Begin writing business code in the workflows located in the *ProcessLayer* folder

*ProcessLayer\InitAllApplications.xaml* - write business code to open all applications needed during processing.

*ProcessLayer\CloseAllApplications.xaml* - write business code to close all applications you have opened at previous step.

*ProcessLayer\ProcessTransaction.xaml* - write business code to use applications that are open and data from io_TransactionItem and complete the transaction. At the end of the transaction, take the applications to the page they were at when you began the transaction. 

3. Execute and have fun! 

