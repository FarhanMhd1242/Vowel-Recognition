# Vowel-Recognition
==========================================================Instruction to execute the code===================================================
The Zip file cintain 2 folders:
1) Vowel Utterances : This folder contains all vowel utterances 
2) Vowel_Recognition : This is the project file.
---------------------------------------------------

Execution Process:

1) Load the project into microsoft visual studio 2010.
2) I already put all the files into project folder i.e. DriveName:\204101022_vowelRecognition\Vowel_Recognition\Vowel_Recognition
3) Now, open the Vowel_Recognition.cpp from solution explorer inside Source Files.
4) Build the code and then Debug the code by choosing "start without debugging".
5) After Executing the code first it will show you 3 options:

	Press 1 : for training
	Press 2 : for offline testing
	Press 3 : for online Testing using Recording_Module

Now here choose any one option between 2 and 3 to continue with the program.

-> why not first option?
   Because I had already performed the training and Dump all 5 files which contains cepstral coefficients of five frames for each vowel.

-> Now, if you choose option 2 then it will perform the testing on my recorded data i.e. testing on all 50 utterances 10 for each vowel and
   at the end it will calculate the accuracy also.

-> And if you choose option 3 the Recording_Module is started for online testing and recording time is 3 seconds.  
  

==============================================================Explaination of My code========================================================

1) Trainig:
   --------
-> firstly I am taking all 10 files of one vowel and performed training, the training goes like as follows:

	-> Skipping some samples like 1000 or 2000 to avoid microphone problem.
	-> Now performing step wise operations to calculate cepstral coefficients.

		1) DC shift.
		2) Normalization
		3) Framing : taking five frames from the steady part.
		4) for each frame calculating Ri's, Ai's and Ci's.

			-> For Ri's, performing Autocorelation analysis.
			-> For Ai's, performing Levinson Durbin Algorithm.
			-> For Ci's, Applying cepstral coefficients formula.

		5) After finding Ci's correctly applying Raised Sine Window on all Ci's for every frame.

-> Now, The end result for this is a 5x12 matrix of cepstral coefficients(i.e. 12 cepstral coefficients for all 5 frames) which will be dumped 
   into a txt file as it is.
   
-> Repeating above process for every vowel.

-> Now, I have 5 different files which contains cepstral coefficients of five frames for each vowel.



2) Offline Testing:
   ----------------
-> for Offline testing I am taking another 10 files of each vowel and performed testing on it, the testing goes like as follows:

	-> firstly calculating Cepstral coefficients of five steady frames for every input file and the process of finding 
	   cepstral coefficients is same as we find in training part.
	-> After that finding the Tokhura Distance with each vowel and the one which gives minimum Tokhura distance is recognized as vowel.  
	-> Repeating above process for every vowel.
 

3) Online Testing:
   ----------------
-> for online testing is done by using Recording_Module.exe:
	-> after Recording a text file is created names as input_file.txt.
	-> Now for this file I am calculating Cepstral coefficients of five steady frames and the process of finding cepstral coefficients is 
           same as we find in training part.
	-> After that finding the Tokhura Distance with each vowel and the one which gives minimum Tokhura distance is recognized as vowel.  
	
==================================================================================================================================================
