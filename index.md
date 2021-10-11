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

Papers that are successfully evaluated will be awarded one or two artifact badges. 
Submission of artifacts is optional and will not change the decision of acception of the original paper.

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

The artifact evaluation is performed in the following two phases.
## Test Phase 
In the test phase, reviewers check if the artifact is functional, i.e., they look for setup problems (e.g., corrupted, missing files, crashes on simple examples, etc.). If any problems are detected, the authors are informed of the outcome and asked for clarification.  

To this end, a github repository will be used, where discovered issues are communicated with the issue and a first notification is given to the authors at 17.01, who then have 5 days to solve the problems and answer to the respective issue. Reviewers and authors are encouraged to use these 5 days for further clarifying comments. 

Github will *not* be used to upload the artifact itself.
    
## Assessment Phase
In the assessment phase, reviewers will try to reproduce any experiments or activities and evaluate the artifact w.r.t the questions detailed above.
The final review is communicated using EasyChair.

## Awarding
FASE awards the [evaluation and availability badges of EAPLS](https://eapls.org/pages/artifact_badges/). 
 * The availability badge will be awarded if the artifact is publically available and has a DOI. We recommend services like [zenodo](https://zenodo.org/) or [figshare](figshare.com) for this.
 * The evaluation badge has two levels, functional and reusable. Each successfully evaluated artifact receives at least the functional bade. The reusable badge is granted to artifacts of very high quality. Authors may use all granted badges on the title page of the respective paper. Detailed guidelines for both levels is described [here](https://eapls.org/pages/artifact_badges/).

Availability and evaluation badges are awareded independent of each other. 

# Artifact Submission
An artifact submission conists of

* An abstract that (1) summarizes the artifact and explains its relation to the paper, (2) document clearly how to perform the test phase (3) document how to reproduce the results of the paper (4) describe which badge the authors submit for, and (5) include
        an URL from which a .zip file containing the artifact can be downloaded - we encourage you to provie a DOI - and
        the SHA256 checksum of the .zip file.
* A .pdf file of the most recent version of the accepted paper, which may differ from the submitted version to take reviewers' comments into account.

Please also look at the Artifact Packaging Guidelines section for detailed information about the contents of the submission.

The abstract and the .pdf file of your paper must be submitted to EasyChair.

Link TBA

We need the checksum to ensure the integrity of your artifact. You can generate the checksum using the following command-line tools.

    Linux: sha256sum <file>
    Windows: CertUtil -hashfile <file> SHA256
    MacOS: shasum -a 256 <file> 

If you cannot submit the artifact as requested or encounter any other difficulties in the submission process, please contact the artifact evaluation chairs prior to submission. 

# Artifact Packaging Guidelines

TBA

## FASE 2022 Virtual Machine
The [FASE 2022 virtual machine]() was created with VirtualBox 6.1.26 and consists of an installation of Ubuntu 20.04.03 with Linux 5.11.0-37 and the following notable packages.

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
- If you have only one package without dependencies but with local modifications, e.g., particular configuration files, you can use the dpkg-repack utility
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
You can get the necessary `.deb` files for example as follows:
 
    pip3 download <package>
The downloaded package can then be installed using
 
    pip3 install <package-file>

### Including Ruby Gem Packages
To provide missing Ruby Gem packages, you may download them via
 
    gem fetch [gem] 
and let the reviewer instal them, e.g., via
 
    gem install <gem-file>
