[Past FASE Artifact Evaluations](./past-aes.html)

# FASE Artifact Evaluation 2023
As in 2022, FASE'23 will have an optional artifact evaluation for accepted papers.

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

Submission of artifacts is optional. We aim to assess the artifacts themselves and not the quality of the research linked to the artifact, which has been assessed by the FASE 2023 program committee. In particular, the result of the artifact evaluation will not alter the already made paper acceptance decision. 
The goal of our review process is to be constructive and to improve the submitted artifacts. Only, if an artifact cannot be improved to achieve sufficient quality in the given time frame or it is inconsistent with the paper, it should be rejected. Furthermore, papers whose artifacts are successfully evaluated will be awarded one or two artifact badges. 

# Important Dates
 * 05.01.2023 - Submission Artifact
 * 16.01.2023 - Test phase notification
 * 16.01 - 19.01.2023 - Communication phase
 * 09.02.2023 - Final Notification

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

To this end, a GitHub repository will be used, where discovered problems are communicated within an issue and a first notification is given to the authors at 16.01.2023, who then have 4 days to solve the problems and answer to the respective issue. Reviewers and authors are encouraged to use these 4 days for further clarifying comments. 

GitHub will *not* be used to upload the artifact itself.
    
## Assessment Phase
In the assessment phase, reviewers will try to reproduce any experiments or activities and evaluate the artifact w.r.t the questions detailed above.
The final review is communicated using EasyChair.

## Awarding
FASE awards the [Artifacts Available and Artifacts Evaluated badges of EAPLS](https://eapls.org/pages/artifact_badges/). 
 * The Artifacts Available badge will be awarded if the artifact is publicly available and has a DOI that is referenced in the respective paper. We recommend services like [zenodo](https://zenodo.org/) or [figshare](https://figshare.com/) for this.
 * The Artifacts Evaluated badge has two levels, functional and reusable. Each successfully evaluated artifact receives at least the functional badge. The reusable badge is granted to artifacts of very high quality. 

Artifacts Available and Artifacts Evaluated badges are awarded independent of each other. Authors may use all granted badges on the title page of the respective paper. Detailed guidelines for both levels are described [here](https://eapls.org/pages/artifact_badges/).

# Artifact Submission
An artifact submission consists of

* An abstract, to be written directly in EasyChair, that 
  1. summarizes the artifact and explains its relation to the paper, 
  2. describes which badge the authors apply for,
  3. mentions where in the artifact it is documented how to perform the test phase and how to reproduce the results of the paper, and
  4. includes an URL - we encourage you to provie a DOI - to a .zip file of your artifact containing
    * a license file that allows the artifact evaluation committee to evaluate the artifact,  
    * a clear documentatation how to perform the test phase 
    * a documentation how to reproduce the results of the paper, and 
  5. the SHA256 checksum of the .zip file.
* A .pdf file of the most recent version of the accepted paper, which may differ from the submitted version to take reviewers' comments into account.

Please also look at the [Artifact Packaging Guidelines](#artifact-packaging-guidelines) for detailed information about the contents of the submission.

The abstract and the .pdf file of your paper must be submitted via EasyChair.

[http://www.easychair.org/conferences/?conf=fase2023](https://easychair.org/my/conference?conf=fase23)

We need the checksum to ensure the integrity of your artifact. You can generate the checksum using the following command-line tools.

    Linux: sha256sum <file>
    Windows: CertUtil -hashfile <file> SHA256
    MacOS: shasum -a 256 <file> 

If you cannot submit the artifact as requested or encounter any other difficulties in the submission process, please contact the artifact evaluation chairs prior to submission. 

# Artifact Packaging Guidelines
We expect that authors package their artifact (.zip file) and write their instructions such that the artifact evaluation committee can evaluate the artifact within the FASE 2023 virtual machine (see [below](#fase-2023-virtual-machine)).
The artifact must contain all the required files to replicate your results in the FASE 2023 virtual machine. 
In particular, the artifact must include all additional software or libraries that are not part of the virtual machine and provide instructions how to install and set them up.
Do not submit a virtual machine image in the .zip file. AEC members will copy your .zip file into the provided virtual machine.
For further information, consider our [recommendations](#recommendations) on the artifact content.

## FASE 2023 Virtual Machine
TBA

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
A LICENSE file describing the rights.  Your license needs to allow the artifact evaluation committee members to download and evaluate the artifact, e.g., download, use, execute, and modify the artifact for the purpose of artifact evaluation. Please refer to typical [open source licenses](https://opensource.org/licenses) where possible. Artifacts without an open source license are also accepted, but a type of license needs to be specified, which allows the committee to assess the artifact.
				
### README
The README file should introduces the artifact to the user, i.e.,  describes what the artifact does, and guides the user through the installation, set up tests, and replication of your results. Ideally, it should consist of the following parts.

* **Summary** briefly describes the artifact goal, authors, reference to the paper, and indication on how to cite the artifact.
* **Setup** describes the steps to set up your artifact within the provided FASE 2023 VM. To simplify the reviewing process, we recommend to provide an installation script (if necessary).
* **Hardware Requirements** state the hardware requirements (RAM, number of cores, CPU frequency), which you considered to test your artifact. Your resource requirements should be modest and allow replication of results even on laptops. 
* **Test Instructions** document how to perform the test phase evaluation, e.g., provide instructions that allow rudimentary testing (i.e., in such a way that technical difficulties would pop up) in as little time as possible.
* **Replication Instructions** clearly describe how to repeat/replicate/reproduce the results presented in the paper.
  * Please document which claims or results of the paper can be replicated with the artifact and how (e.g., which experiment must be performed). Please also explain which claims and results cannot be replicated and why.
  * Describe in detail how to replicate the results in the paper, especially describe the steps that need to be performed to replicate the results in the paper. To simplify the reviewing process, we recommend to provide evaluation scripts (where applicable).
  * Please provide for each task/step of the replication (an estimate) how long it will take to perform it or how long it took for you and what exact machine(s) you used.	
* **Replication with Limited Resources** For tasks or experiments that require a large amount of resources (hardware or time), we additionally recommended to offer a possibility to replicate a subset of the results of the paper that can be reproduced in a reasonable amount of time (e.g., within 8 hours) on various hardware platforms including laptops. In this case, please also include a script to replicate only a subset of the results. If this is not possible, please contact the artifact evaluation chairs early, but no later than before submission.
* **Examples of Usage** describe how to use your artifact in general accompanied by small examples.

# Artifact Evaluation Committee

## Chairs
* Marie-Christine Jakobs (Technische Universität Darmstadt, Germany)
* Carlos Diego Nascimento Damasceno (Radboud University)

## Members
TBA
