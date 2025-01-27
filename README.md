# SyzVegas: Beating Kernel Fuzzing Odds with Reinforcement Learning

Fuzzing embeds a large number of decisions requiring finetuned and hard-coded parameters to maximize its efficiency. This is especially true for kernel fuzzing due to (1) OS kernels’ sheer size and complexity, (2) a unique syscall interface that requires special handling (e.g., encoding explicit dependencies among syscalls), and (3) behaviors of inputs (i.e., test cases) are often not reproducible due to the stateful nature of OS kernels. Hence, Syzkaller, the state-of-art gray-box kernel fuzzer, incorporates numerous procedures, decision points, and hard-coded parameters master-crafted by domain experts. Unfortunately, hard-coded strategies cannot adjust to factors such as different fuzzing environments/targets and the dynamically changing potency of tasks and/or seeds, limiting the overall effectiveness of the fuzzer. In this paper, we propose SYZVEGAS, a fuzzer that dynamically and automatically adapts two of the most critical decision points in Syzkaller, task selection and seed selection, to remarkably improve coverage reached per unit-time. SYZVEGAS’s adaptation leverages multi-armed-bandit (MAB) algorithms along with a novel reward assessment model. Our extensive evaluations of SYZVEGAS on the latest Linux Kernel and its subsystems demonstrate that it (i) finds up to 38.7% more coverage than the default Syzkaller, (ii) better discovers bugs/crashes (8 more unique crashes) and (iii) has very low 2.1% performance overhead. We reported our findings to Google’s
Syzkaller team and are actively working on pushing our changes upstream.

Based on syzkaller version at 2020/01/08

WIP pull request:
- https://github.com/google/syzkaller/pull/1895
