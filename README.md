## Patch Vulnerability Commit Reconciliation: A quantitative approach to identifying vulnerable commits in open source software projects.

## Partnership
This project is in direct partnership with the [Vulnerability History Project](https://github.com/VulnerabilityHistoryProject).

## Overview
To our knowledge, no tool exists that allows a user to provide a Git commit hash that fixes a bug or vulnerability and returns the commit(s) that contributed to the vulnerability.

## Defined Aspects of the Problem
- **Patch Commit:** The commit that successfully fixes the vulnerability.
- **Source of Patch Commit:** The commit is scraped from the [National Vulnerability Database](https://nvd.nist.gov/).
- **Connection to CVE:** The commit is explicitly tied to a CVE entry.

## Key Contributions
- Introducing **confidence scores** to quantify the likelihood that a commit introduced a vulnerability.
- Providing detailed **quantitative metrics** for evaluating accuracy in vulnerability detection systems.
- Handling cases where existing SZZ implementations fall short, such as vulnerability-inducing commits that **remove code, refactor code, or perform complex changes**.
- Designing new methods/algorithms to quantify and contextualize **why** a vulnerability-inducing commit cannot be identified when existing SZZ techniques fail.

## Data Collection
Data collection has already been completed via the [Vulnerability History Project](https://github.com/VulnerabilityHistoryProject/mega-foss/blob/master/src/slurm/drill_scripts/viable_patches.json).

## Implementation Plan
- [x] Data collection (completed via the Vulnerability History Project)
- [ ] Define specific **metrics** for evaluating confidence scores and commit classification --> IN PROGRESS
- [ ] Implement **initial SZZ-based vulnerability identification** using PyDriller
- [ ] Develop a **funnel-based approach** to identify the type of vulnerability based on the patch commit
- [ ] Integrate various SZZ implementations to select the appropriate one per vulnerability type
- [ ] Design **new algorithms** for cases where existing SZZ methods fail
- [ ] Quantify and contextualize failures, creating metrics that explain why a commit **cannot be identified**
- [ ] Validate results and refine confidence metrics

## Funnel-Based Approach
- This tool acts as a **funnel**:
  - It first identifies the type of vulnerability based on the **patch commit** (which was acquired in the data collection phase).
  - If the vulnerability can be identified using **existing SZZ algorithms**, the proper one will be called.
  - If existing SZZ techniques **fail to identify the vulnerability**, new methods will be designed to:
    - Identify the vulnerability-inducing commit
    - Provide **quantitative metrics** explaining why it cannot be found
    - Contextualize failure cases to improve accuracy

## Tools & Dependencies
- **PyDriller**: Core tool for analyzing Git repositories and commit histories.
- **Multiple SZZ Implementations**: Different SZZ versions will be applied at various stages of the pipeline.

## References
- **TC-SZZ Paper** (To be included in final citation list)
- Additional research on confidence metrics and vulnerability detection techniques
