# kubectl-restarts

> Sort the crash loops by how hard they are crashing.

**Status:** 🚧 In development

## Overview

Rank pods by restart count with the last termination reason and exit code, turning a wall of CrashLoopBackOff into an ordered list of what to look at first.

## Features

- Ranks pods by container restart count across one namespace or the whole cluster
- Shows each container's last terminated reason, exit code and finish time
- Separates OOMKilled from non-zero application exits and from liveness-probe kills
- Rolls restarts up to the owning Deployment, StatefulSet or DaemonSet
- `--since` window so a crash loop that already settled drops off the list
- Table, wide and JSON output for pasting into an incident note

## Stack

Go + cobra, `k8s.io/client-go`, `k8s.io/cli-runtime` (genericclioptions, so it honours the usual kubectl flags).

## Usage

```bash
kubectl restarts --all-namespaces --since 24h --sort-by count --top 20
```

## License

MIT
