# -*- coding: utf-8 -*-
"""
Created on Thu Dec 18 16:10:49 2014

@author: Shreyas Ragavan
"""
# This program basically allows the user to apply a single ANSYS CFD Post state/session file on multiple result files in a location, one after the other.

###---------- USER INPUT -------------###

#Enter the path to the location of the CFD Post executable in the ANSYS installation location
CFDPost_loc=r'"C:\Program Files\ANSYS Inc\v145\CFD-Post\bin\cfdpost"'

#Enter the path to the location of the ANSYS CFD Post session (.cse) or state (.cst) file
Post_template_loc=r'"C:\Post_Processing_Templates\FP_session_v13_TEST_2.cse"'

#Enter the location of all the result files
Res_loc=r'Q:\Queueing_sys\Completed\'


###---x---x--x-- USER INPUT -x---x---x---x--###

#importing required libraries
import os
import time as t
import glob
import subprocess as sp

#Creating BAT script for extracting the list of res files in the current working folder - sorted Date wise
def res_list_syn():
    print ""
    print "Grabbing all res files from chosen location."
    os.chdir(Res_loc)
    variableA1=glob.glob('*.res')
    post_syn(variableA1)
    
def post_syn(variable):
    print " "    
    print "Listing grabbed res files and creating Post BAT file in chosen location..." 
    print ""
    post_batname='Post_bat_runner.BAT'   
    post_bat_loc=os.path.join(Res_loc,post_batname)
    PC=open(post_bat_loc,'w')
    PC.write('cd /d "%s"\n'%Res_loc)
    i=0
    while i<len(variable):
        print "%d --%s" %(i,variable[i])
        PC.write('%s -s %s %s\n' %(CFDPost_loc,Post_template_loc,variable[i]))
        i+=1
    PC.close()
    print "Running post macro on all the listed Res Files...."
    print ''
    sp.call(post_bat_loc)
    t.sleep(5)
    print 'Killing temp files...'
    t.sleep(5)
    File_killer(Res_loc,'BAT')
    

#Function for deleting temp Files. Prevents Clutter.
def File_killer(variable1, variable2):
    for variable in glob.glob('%s/*.%s'%(variable1,variable2)):
        if os.path.isfile(variable):
            os.remove(variable)

#Starting Program. Geting current working directory
print "Hello. Program Launch... Getting Current working directory.-->"
print ""
currentwd=os.getcwd()
print "Current working directory is : %s"%currentwd
print ""
res_list_syn()
