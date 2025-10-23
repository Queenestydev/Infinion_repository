# Infinion_repository
Repository for  Assessment
# Self-Hosted GitHub Actions Runner — INFINION Assessment
**Candidate:** Queenesther Akachukwu  
**Role applied for:** Graduate Trainee (DevOps)  
**Date submitted:** 23 October 2025

## Summary
This repository demonstrates a self-hosted GitHub Actions runner configured on my local PC and a sample pipeline that executes on that runner. The workflow file is `.github/workflows/selfhosted-test.yaml`.

## How I set it up (step-by-step)
On GitHub (repo: `Queenestydev/Infinion_repository`) → Settings → Actions → Runners → **New self-hosted runner**. I selected Linux and copied the platform-specific download and configuration commands shown by GitHub.  
On my PC (Linux), created a directory `actions-runner`, downloaded the runner package, and ran the `config` command GitHub supplied (this uses a short-lived registration token). Then I tested with `./run.sh` (on Linux). 
Added `self-hosted-test.yaml` workflow that targets `runs-on: [self-hosted, linux, x64]`. Pushed to `main` and confirmed the job ran on my self-hosted runner.
## Files changed / created
- `.github/workflows/self-hosted-test.yaml` — smoke test workflow
- `actions-runner/` — local runner files (not committed; present on my PC)
- `README.md` — this file

## Challenges I faced & how I solved them
**Short-lived registration token** — the token GitHub generates is temporary. I copied the token and ran the setup immediately; if it expired I created a new runner from the UI and re-ran the config command. 
**Security concerns with persistent host** — to reduce risk, I cleaned workspaces between runs and limited runner access to this repository only. 
## What I would do differently in a production environment
- **Ephemeral runners:** Use ephemeral cloud runners (auto-created containers/VMs) or an autoscaling fleet so each job runs in a fresh environment (reduces contamination risk). 
- **Isolated build environment:** Run each job inside a container or VM image that<img width="657" height="413" alt="repo 3" src="https://github.com/user-attachments/assets/2425191f-000c-4f50-a652-0dc054652901" />
<img width="659" height="406" alt="repo 2" src="https://github.com/user-attachments/assets/36d8d0f8-279c-41d9-97c1-a36264f92254" />
<img width="650" height="407" alt="repo 1" src="https://github.com/user-attachments/assets/737a3bd6-a4cf-4df8-bd4d-5fab2404476d" />
 is destroyed after use.  
- **Secret management & short-lived credentials:** Use short-lived cloud credentials or secrets managers and avoid mounting long-lived secrets on runner hosts.  
- **Monitoring & central logging:** Ship runner logs to central monitoring and perform intrusion detection.

## Security measures implemented
- Limited repository-level access to this runner (registered it at repo scope only). 
- Did not store secrets on the runner host; secrets provided via GitHub Secrets.  
- Installed the runner under a dedicated low-privilege account.  
## How to test the setup
1. Push a change to `main` (or trigger the workflow manually in Actions).  
2. Confirm in GitHub Actions UI that the job ran and the runner picked the job.  

## References
- GitHub Docs — Adding self-hosted runners. :contentReference[oaicite:30]{index=30}  
- GitHub Docs — Runner requirements and network. :contentReference[oaicite:31]{index=31}  
- GitHub Docs — Using self-hosted runners in a workflow (labels). :contentReference[oaicite:32]{index=32}  
- GitHub Docs — Secure use reference and runner group controls. :contentReference[oaicite:33]{index=33}

- ![IMG-20251023-WA0007](https://github.com/user-attachments/assets/2ae8f7cc-ab3d-45ba-9321-6c8f983ab7f2)
![IMG-20251023-WA0006](https://github.com/user-attachments/assets/b74b40e3-9fe7-4704-a95a-c7e50164242c)
![IMG-20251023-WA0005](https://github.com/user-attachments/assets/4d4ad709-9784-4f02-b46a-4966e0e39bfd)
![IMG-20251023-WA0004](https://github.com/user-attachments/assets/1019a1e2-efd1-404a-8b4f-311edc6cf148)
![IMG-20251023-WA0003](https://github.com/user-attachments/assets/6dfd27da-809a-4619-bd5f-18b62adebba6)
![IMG-20251023-WA0002](https://github.com/user-attachments/assets/be5fc04b-573e-41c4-aad4-1c2ccecb98e3)
![IMG-20251023-WA0001](https://github.com/user-attachments/assets/c81eb0d9-497c-4d3b-b827-920f4417e872)
<img width="656" height="405" alt="repo 4" src="https://github.com/user-attachments/assets/0410dd66-8b23-4bef-ad06-31beb1e04ffa" />
<img width="657" height="413" alt="repo 3" src="https://github.com/user-attachments/assets/25338a73-e683-409a-8f3b-b6d6c57d3f4e" />
<img width="659" height="406" alt="repo 2" src="https://github.com/user-attachments/assets/2a53fe31-7d71-4dfa-8178-217642f6bf21" />
<img width="650" height="407" alt="repo 1" src="https://github.com/user-attachments/assets/5ed31740-f3da-49e4-a780-790761f66a97" />


