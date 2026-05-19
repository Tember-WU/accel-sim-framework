# Baseline Setup

Date: 2026-05-15

Environment:
- Windows 11 host
- Docker Desktop
- VSCode Dev Container
- Accel-Sim official Docker image:
  ghcr.io/accel-sim/accel-sim-framework:ubuntu-24.04-cuda-12.8

Repositories:
- accel-sim-framework
- gpgpu-sim_distribution

Current branch:
- shuwei-study

Status:
- short-tests.sh passes successfully



# Issues Encountered

## CRLF / LF issue

Problem:
- shell scripts failed with:
  $'\r': command not found

Cause:
- Windows CRLF line endings

Fix:
apt install -y dos2unix
find . -type f | xargs dos2unix





# Docker Workflow

Start container:
docker start -ai accelsim

Run new container:
docker run --name accelsim -it \
-v D:\Accel-sim-refactor\accel-sim-framework:/accel-sim/accel-sim-framework \
ghcr.io/accel-sim/accel-sim-framework:ubuntu-24.04-cuda-12.8 \
/bin/bash






# Repository Structure

Outer repo:
- accel-sim-framework

Inner repo:
- gpu-simulator/gpgpu-sim

Important folders:
- gpu-simulator/
- util/
- util/job_launching/
- configs/






# short-tests.sh Workflow

1. setup_environment.sh
2. make simulator
3. download rodinia traces
4. run_simulations.py
5. monitor_func_test.py