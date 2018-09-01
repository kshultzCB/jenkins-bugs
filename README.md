# [ZD-64922](https://cloudbees.zendesk.com/agent/tickets/64922) How to tag from multibranch Pipeline

User wants to tag and push a commit from a multibranch Pipeline.  Some
of the scenarios that need to be handled and may encounter surprises
include:

* Merge commits may be made locally in the multibranch Pipeline
  workspace which are not pushed to the remote repository

* No branch is defined in the workspace of the multibranch Pipeline
  unless the local branch extension is used.  Without a local branch
  there is no obvious name to descrie the remote destination which
  should receive commits that only exist locally