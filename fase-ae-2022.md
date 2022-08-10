[Current Artifact Evaluation](./index.html)

[Past FASE Artifact Evaluations](./past-aes.html)

# FASE Artifact Evaluation 2022
Based on positive experiences of the community, FASE'22 will have an optional artifact evaluation for accepted papers.

The goal of the artifact evaluation is twofold. 
On the one hand, we want to encourage authors to provide more substantial evidence to their papers and to reward authors who create artifacts. 
On the other hand, we want to simplify the independent replication of results presented in the paper and to ease future comparison with existing approaches.

Artifacts of interest include (but are not limited to):
* Software, Tools, or Frameworks
* Data sets
* Test suites
* Machine-checkable proofs
* Any combination of them
* Any other artifact described in the paper

Submission of artifacts is optional. We aim to assess the artifacts themselves and not the quality of the research linked to the artifact, which has been assessed by the FASE 2022 program committee. 
The goal of our review process is to be constructive and to improve the submitted artifacts.
Only, if an artifact cannot be improved to achieve sufficient quality  in the given time frame or it is inconsistent with the paper, it should be rejected.
Further note, artifact evaluation will not change the decision of accepting the original paper. 
However, papers that are successfully evaluated will be awarded one or two artifact badges. 

# Important Dates
 * 05.01.22 - Submission Artifact
 * 17.01 - Test phase notification
 * 17.01 - 21.01.22 - Communication phase
 * 16.02.22 - Final Notification

# Artifact Evaluation

All artifacts are evaluated by the artifact evaluation committee. Each artifact will be reviewed by at least two committee members. Reviewers will read the accepted paper and explore the artifact to evaluate how well the artifact supports the claims and results of the paper. The evaluation is based on the following questions.

* Is the artifact consistent with the paper and the claims made by the paper?
* Are the results of the paper replicable through the artifact?
* Is the artifact complete, i.e., how many of the results of the paper are replicable?
* Is the artifact well-documented?
* Is the artifact easy to use?
* Is the artifact publicly and permanently available?

The artifact evaluation is performed in the following two phases.
## Test Phase 
In the test phase, reviewers check if the artifact is functional, i.e., they look for setup problems (e.g., corrupted, missing files, crashes on simple examples, etc.). If any problems are detected, the authors are informed of the outcome and asked for clarification.  

To this end, a GitHub repository will be used, where discovered problems are communicated within an issue and a first notification is given to the authors at 17.01, who then have 5 days to solve the problems and answer to the respective issue. Reviewers and authors are encouraged to use these 5 days for further clarifying comments. 

GitHub will *not* be used to upload the artifact itself.
    
## Assessment Phase
In the assessment phase, reviewers will try to reproduce any experiments or activities and evaluate the artifact w.r.t the questions detailed above.
The final review is communicated using EasyChair.

## Awarding
FASE awards the [evaluation and availability badges of EAPLS](https://eapls.org/pages/artifact_badges/). 
 * The availability badge will be awarded if the artifact is publicly available and has a DOI. We recommend services like [zenodo](https://zenodo.org/) or [figshare](https://figshare.com/) for this.
 * The evaluation badge has two levels, functional and reusable. Each successfully evaluated artifact receives at least the functional badge. The reusable badge is granted to artifacts of very high quality. Authors may use all granted badges on the title page of the respective paper. Detailed guidelines for both levels are described [here](https://eapls.org/pages/artifact_badges/).

Availability and evaluation badges are awarded independent of each other. 

# Artifact Submission
An artifact submission consists of

* An abstract in form of a .pdf file that 
  1. summarizes the artifact and explains its relation to the paper, 
  2. describes which badge the authors submit for,
  3. mentions where in the artifact it is documented how to perform the test phase and how to reproduce the results of the paper, and
  4. includes an URL - we encourage you to provie a DOI - to a .zip file of your artifact containing
    * a license file that allows the artifact evaluation committee to evaluate the artifact,  
    * a clear documentatation how to perform the test phase 
    * a documentation how to reproduce the results of the paper, and 
  5. the SHA256 checksum of the .zip file.
* A .pdf file of the most recent version of the accepted paper, which may differ from the submitted version to take reviewers' comments into account.

Please also look at the [Artifact Packaging Guidelines](#artifact-packaging-guidelines) for detailed information about the contents of the submission.

The abstract and the .pdf file of your paper must be submitted via EasyChair.

[http://www.easychair.org/conferences/?conf=fase2022](http://www.easychair.org/conferences/?conf=fase2022)

We need the checksum to ensure the integrity of your artifact. You can generate the checksum using the following command-line tools.

    Linux: sha256sum <file>
    Windows: CertUtil -hashfile <file> SHA256
    MacOS: shasum -a 256 <file> 

If you cannot submit the artifact as requested or encounter any other difficulties in the submission process, please contact the artifact evaluation chairs prior to submission. 

# Artifact Packaging Guidelines

We expect that authors package their artifact (.zip file) and write their instructions such that the artifact evaluation committee can evaluate the artifact within the [FASE 2022 virtual machine](https://doi.org/10.5281/zenodo.5561969) (see [below](#fase-2022-virtual-machine)).
The artifact must contain all the required files to replicate your results in the FASE 2022 virtual machine. 
In particular, the artifact must include all additional software or libraries that are not part of the virtual machine and provide instructions how to install and set them up.
Do not submit a virtual machine image in the .zip file. AEC members will copy your .zip file into the provided virtual machine.
For further information, consider our [recommendations](#recommendations) on the artifact content.

## FASE 2022 Virtual Machine
The [FASE 2022 virtual machine](https://doi.org/10.5281/zenodo.5561969) was created with VirtualBox 6.1.26 and consists of an installation of Ubuntu 20.04.03 with Linux 5.11.0-37 and the following notable packages.

* A 32bit libc
* clang 12.0.0
* gcc 9.3.0
* Mono 6.12.0.122
* OCaml 4.13.1 and OPAM 2.1.0 
* OpenJDK 11.0.11 (default), and OpenJDK 16.0.1 

    To switch between Java runtimes, you can use  `sudo update-alternatives --config java`.
    To switch between Java compilers, you can use  `sudo update-alternatives --config javac`.
* Python 2.7.18, Python 3.8.10, and pip3 (pip 20.0.2)
* Ruby 2.7.0p0
* bash 5.0.17(1)	
* cmake 3.16.3
* GNU Make 4.2.1
* BenchExec 3.9
* VIM 8.1
* Emacs 26.3
* VirtualBox guest additions 6.1.26

The login and password of the default user are: `fase2022` / `fase2022`. The root user has the same password. 

In order to save space, the VM does not have an active swap file. Please mention in your submission if you expect that a swap file is needed. You can activate swap for the running session using the following commands.

    sudo fallocate -l 1G /swapfile
    sudo chmod 600 /swapfile
    sudo mkswap /swapfile
    sudo swapon /swapfile
    
The artifact evaluation committee will be instructed not to download software or data from external sources. Any additional software required by your artifact must be included in the `.zip` file and the artifact must provide instructions for the installation. 

### Including Ubuntu Packages
To include an Ubuntu package in your artifact submission, you can provide a `.deb` file with all the necessary dependencies from inside the VM. Reviewers can then install them as follows.

    sudo dpkg -i <.deb file>
    
You can get the necessary `.deb` files for example as follows:
- If you have only one package without dependencies, you can use
    `apt-get download <packagename>`
- If you have only one package without dependencies but with local modifications, e.g., particular configuration files, you can use the dpkg-repack utility.
- If you have a package with multiple dependencies, you can use wget together with apt to download them all and put them into a folder:
```
    wget $(apt-get install --reinstall --print-uris -qq <packagename> | cut -d"'" -f2)
```
Alternatively, you may run the following code.
```
    sudo apt-get update
    apt-get --print-uris install <packagename> | grep -oP "(?<=').*(?=')" > <filename>
    for i in $(cat <filename>) ; do wget -nv $i ; done
```

### Including OCaml Packages
You can include required OCaml packages not present in our installation via OPAM. To this end, you may want to download the packages, e.g., using the following command.

    opam install --download-only --destdir=<dir> <package>
    
 The reviewers may than use the following command to install all packages available in `<dir>`.
 
    opam install <dir>
 
### Including Python Packages
You may include the required Python packages using pip.
You can get the necessary files for example as follows:
 
    pip3 download <package>
    
The downloaded package can then be installed using
 
    pip3 install <package-file>

### Including Ruby Gem Packages
To provide missing Ruby Gem packages, you may download them via
 
    gem fetch <gem>
    
and let the reviewer install them, e.g., via
 
    gem install <gem-file>

## Recommendations
We recommend to prepare your artifact in such a way that any computer science expert without dedicated expertise in your field can use your artifact, especially replicate your results. For example, keep the evaluation process simple, provide easy-to-use scripts and a detailed README document. Furthermore, the artifact and its documentation should be self-contained.

Next to the main artifact, i.e., data, software, libraries, scripts, etc. required to replicate the results of your paper and any additional software required by your artifact including an installation description, we recommend to include the following elements.

### License File
A LICENSE file describing the rights. Your license needs to allow the artifact evaluation chairs to download and distribute the artifact to the artifact evaluation committee members and the artifact evaluation committee members must be allowed to evaluate the artifact, e.g., use, execute, and modify the artifact for the purpose of artifact evaluation.

				
### README
The README file should introduces the artifact to the user, i.e.,  describes what the artifact does, and guides the user through the installation, set up tests, and replication of your results. Ideally, it should consist of the following parts.

* It should describe the steps to set up your artifact within the provided FASE 2022 VM. To simplify the reviewing process, we recommend to provide an installation script (if necessary).
* It should state the hardware requirements (RAM, number of cores, CPU frequency), which you considered to test your artifact. Your resource requirements should be modest and allow replication of results even on laptops. 
* It should document how to perform the test phase evaluation, e.g., provide instructions that allow rudimentary testing (i.e., in such a way that technical difficulties would pop up) in as little time as possible.
* It should contain a clear description how to repeat/replicate/reproduce the results presented in the paper.
  * Please document which claims or results of the paper can be replicated with the artifact and how (e.g., which experiment must be performed). Please also explain which claims and results cannot be replicated and why.
  * Describe in detail how to replicate the results in the paper, especially describe the steps that need to be performed to replicate the results in the paper. To simplify the reviewing process, we recommend to provide evaluation scripts (where applicable).
  * Please provide for each task/step of the replication (an estimate) how long it will take to perform it or how long it took for you and what exact machine(s) you used.	
* For tasks or experiments that require a large amount of resources (hardware or time), we additionally recommended to offer a possibility to replicate a subset of the results of the paper that can be reproduced in a reasonable amount of time (e.g., within 8 hours) on various hardware platforms including laptops.	 In this case, please also include a script to replicate only a subset of the results. If this is not possible, please contact the artifact evaluation chairs early, but no latter than before submission.
* Ideally, it describes how to use your artifact in general accompanied by small examples.

# Artifact Evaluation Committee

## Chairs
* Marie-Christine Jakobs (Technische Universität Darmstadt, Germany)
* Eduard Kamburjan (University of Oslo, Norway)

## Members
* Chinmayi Baramashetru (University of Oslo, Norway)
* Saverio Giallorenzo (Università di Bologna, Italy, and Inria, France)
* Pablo Gómez-Abajo (Universidad Autónoma de Madrid, Spain)
* Elena Gómez-Martínez (Universidad Autónoma de Madrid, Spain)
* Jan Haltermann (Carl von Ossietzky Universität Oldenburg, Germany)
* Hannes Kallwies (Universität zu Lübeck, Germany)
* Dylan Marinho (LORIA, Université de Lorraine, France)
* Felix Pauck (Universität Paderborn, Germany)
* Sven Peldszus (Universität Koblenz-Landau, Germany)
* Mohammad Rezaalipour (Università della Svizzera italiana, Switzerland)
* Cedric Richter (Carl von Ossietzky Universität Oldenburg, Germany)
* Maya Retno Ayu Setyautami (Universitas Indonesia, Indonesia)
* Asmae Heydari Tabar (Technische Universität Darmstadt, Germany)
* Matthias Volk (Universiteit Twente, The Netherlands)
* Xiuheng Wu (Nanyang Technological University, Singapore)
* Liu Ye (Nanyang Technological University, Singapore)
