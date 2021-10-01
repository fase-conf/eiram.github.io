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
