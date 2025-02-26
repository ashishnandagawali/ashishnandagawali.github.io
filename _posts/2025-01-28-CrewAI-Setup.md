---
layout: post
title: CrewAI Installation Using Anaconda
date: 2025-01-28 20:00:00
description: This blog post describes CrewAI Installation Using Anaconda
tags: CrewAI Installation, Anaconda
categories: CrewAI
featured: false
---
In this article CrewAI Installation Using Anaconda.

> Install anaconda from [Anaconda Download](https://www.anaconda.com/download).

2.  Start powershell from anaconda folder ( similar to below)
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/Start-Menu-Ananconda-Powershell.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

3.  We'll create a new conda environment for crewai. Not a necessary steps but for a safety net, not impacting our existing ongoing conda envionment or python development work due to any dependencies packages or libraries  installation.
4.  Give following command to create new environment called "crewai-handson". In case you are looking for specific version of python you can mention same. 
    ~~~python
        conda create -n crewai-handson
    ~~~
    OR
    ~~~python
        conda create -n crewai-handson   python=3.11.9 
    ~~~
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/conda-crewai-env.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>


5.  Now activate this new environment using command 

    ~~~python
        conda activate crewai-handson
    ~~~
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/conda-crewai-env-activate.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

6.  I am using cursor ide for development of my crewai projects. Cursor ai ( build on VS code) have it own terminal where you can activate your conda environment or use the anaconda shell in separate command or terminal window. Your choice of convenience.

7.  If your cursor or windows command is not able to recognise conda command then add conda location to your environment variable in path.
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/env-variable.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

8.  Either in powershell/command prompt/"cursor terminal", execute command ( If not done sucessfully as Step#5) 

    ~~~python
        conda activate crewai-handson
    ~~~

    Cursor Terminal
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/conda-crewai-env-activate-cursor-term.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>  
    Windows Powershell Command Prompt
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/conda-crewai-env-activate-powershell.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
    Anaconda Powershell Command Prompt
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/conda-crewai-env-activate-anaconda-powershell.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

9.  Now let's install packages required for crewai using pip ( if pip is not installed, install pip using command - "conda install pip"
 

    ~~~python
        Pip install crewai  'crewai[tools]'
    ~~~
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/crewai-install-pip.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

10.  One of the cool feature of crewai is that it gives you a boilerplate code using crewai command so that you don’t have to create a skeleton code. You can run the command -  crewai create crew "ashish-sample-crewai" and it will create a crewai project name `"ashish-sample-crewai"` and with all the basic skeleton code with it.
 
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/crewai-new-prj-creation.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/crewai-new-prj-creation-002.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>    
</div>

11.  By default crewai uses OpenAI api. However in above crewai projection creation, I used the Deep seek LLM so I need to add environment files and give the my Deep Seek LLM api keys. Else it will try to connect to openAI llm and you will get authenticatoin error as you have not mentioned OpenAI API keys. <br><br> Congratulation, you have created crewai project successfully. 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/crewai-project-successful-creation.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

12.  If you want to run this simply give command - `crewai run`  Crewai will do the build and then you can run .
 
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/conda-crewai-run.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>    
</div>

13.  I received the OpenAI api error as expected because I didn’t provide api keys. <br> However it shows crewai set-up is correct and working as desired. 
 
<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/crewai-setup/crewai-run-final.png" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>    
</div>
