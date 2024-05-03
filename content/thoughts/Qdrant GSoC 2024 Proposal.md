---
title: Qdrant GSoC 2024 Proposal
date: 2024-02-22
tags:
  - seed
enableToc: false
--
  
**Personal Information**

- Name: Karan Janthe

- Email: karanjanthe@gmail.com

- Github: [KMJ-007](https://github.com/KMJ-007)

- Blog: [blog](https://kmj-007.github.io/)

- Location: Gujarat, India

- Time Zone: UTC+05:30

- University: Vishwakarma Government Engineering College

- Major: Computer Science And Technology

  

**Project Description**

- Name: WASM-based dimension reduction viz

- Possible Mentors: [Andrey Vasnetsov](https://github.com/generall), [Kartik Gupta](https://github.com/kartik-gupta-ij)

- Goal:

- Implement a dimension reduction algorithm in Rust and compile to WASM, Integrate the WASM code with Qdrant Web UI.

- Have a more efficient and smoother implementation using WASM so it can handle more points and higher dimensions efficiently.

  
  

**ABOUT ME & WHY I CHOSE THIS PROJECT**

I'm Karan Janthe, currently an undergraduate at Vishwakarma Government Engineering College in Ahmedabad, India. I had been fascinated by computers since I was 14; It has given me ability to create things which i can imagine. I'm a strong believer in "standing on the shoulders of giants" — acknowledging that our advancements are built on the work of those who came before us. I'm committed to giving back to the community that has given me so much, which is why I've been actively contributing to open-source projects.

You can see my journey on my [GitHub](https://github.com/KMJ-007) profile, where I share most of my projects. One project I'm particularly proud of is my first hackathon winner project, a [Rag based PDF question-answer app](https://devfolio.co/projects/warplearn-a56b), which introduced me to Qdrant. This experience sparked my interest in vector databases and led me down the path to local-first software, CRDTs, and ultimately to WebAssembly (WASM).

In my free time, I'm channeling my curiosity into building a client-side semantic search using WASM, and experimenting with lightweight ONNX models for efficiency. My latest Rust adventure is [RustyScheme](https://github.com/KMJ-007/RustyScheme), a Lisp interpreter I built to get hands-on with Rust, which was supported by invaluable feedback from the Reddit community ([Built a Lisp Interpreter in Rust – Roast my Code!](https://www.reddit.com/r/rust/comments/1ae52te/built_a_lisp_interpreter_in_rust_roast_my_code/)). Currently, I'm taking a course on data mining where I'm delving into dimensionality reduction among other algorithms. This theoretical backdrop is why I’m drawn to this project. I believe that applying these concepts to a real-world problem will solidify my understanding and connect theoretical knowledge with practical application.

Beyond coding, I've served as the Technical Lead for the Google Developer Student Club at my college, organising numerous events and workshops like the one on [Git and GitHub](https://www.instagram.com/p/Cn_3-UTgUda/?img_index=2). I'm also an active member of the [rocketry club](https://www.instagram.com/vgecrocketry/), where I've worked on avionics for model rockets.

Working Environment And Schedule

--------------------------------

I’ll be mostly working on the code on weekdays nights (Monday to Friday). On weekends, I’ll be focusing on documentation, testing and bug fixing. My awake hours would usually be in between 10 PM IST (4:30 PM UTC) to 3 AM IST the next day (9:30 PM UTC) and I’m comfortable working anytime during this period, in morning i have my college and other lectures which i need to attend.

Except for a few days of traveling (which I’ll be informing in advance to my mentor), I’ll be having no other absences. Anyhow, in cases of emergency, I’ll responsibly notify my mentor of the same with enough detailing.

## Plan:

- **Study Qdrant's Current Web UI Implementation**: Begin by examining the current Qdrant Web UI to understand its functionality and how dimensionality reduction is currently being implemented and visualized.
- **Optimization Research**: Delve into various methods for optimizing t-SNE, drawing insights from the work of [kartik](https://github.com/qdrant/qdrant-web-ui/pull/112). As [generall](https://github.com/qdrant/qdrant-web-ui/pull/112#issuecomment-1887262530) highlighted, the focus will be on refining the implementation rather than the algorithm itself for improved performance.
- **Algorithmic Study and Adaptation**: Thoroughly review the [wasm-bhtsne's approach](https://github.com/Lv-291/wasm-bhtsne), which is based on speeding up t-SNE through tree-based algorithms. Evaluate the potential of adapting this with a multi-threaded capability for more efficient performance.
- **Testing and Benchmarking Preparation**: Set up a robust testing framework to address issues like hard-coded parameters and crashes with smaller datasets. Rigorous benchmarking will help to track and optimize performance enhancements.
- **Implementation and Integration**: Upon completing the optimized algorithm, package the solution as a Rust crate, compile it to WASM, and integrate it with the Qdrant Web UI, ensuring seamless functionality.
  

### Approximate Schedule:

**Week 1 (5/29-6/4)**:

- **Planning and Initialization**: Identify specific performance bottlenecks in the current t-SNE implementation and begin planning for multi-threaded enhancements. Draft a detailed roadmap with milestones for the project.

**Week 2 (6/5-6/11)**:

- **Environment Setup**: Configure development and testing environments. Review existing Rust implementations and understand the nuances of compiling Rust to WASM.

**Week 3 (6/12-6/18)**:

- **Algorithm Study**: Deepen the understanding of tree-based t-SNE algorithms. Begin adapting the concepts for a Rust-based implementation that supports threading.

**Week 4 (6/19-6/25)**:

- **Prototype Development**: Start coding the Rust version of the algorithm. Establish foundational work on multi-threading and parallelism.

**Week 5 (6/26-7/2)**:

- **Iterative Testing**: Implement the initial testing framework. Conduct early tests to detect issues and improve thread management.

**Week 6 (7/3-7/9)**:

- **Performance Tuning**: Benchmark the initial prototype and optimize based on findings. Refine the code for better memory and thread efficiency.

**Week 7 (7/10-7/16)**:

- **Further Development**: Continue building and refining the algorithm. Expand testing to include edge cases and dataset variability.

**Week 8 (7/17-7/23)**:

- **Integration Preparation**: Prepare for the integration of the WASM module into the Qdrant Web UI. Start developing the interface for the integration.

**Week 9 (7/24-7/30)**:

- **WASM Compilation**: Compile the Rust implementation to WASM. Test the compiled module in a local development version of Qdrant Web UI.

**Week 10 (7/31-8/6)**:

- **Integration and User Interface**: Integrate the WASM module with the Web UI. Focus on the user interface and interaction design to ensure a smooth user experience.

**Week 11 (8/7-8/13)**:

- **Community Feedback**: Share the updated visualization with the community. Gather feedback and iterate on the interface and functionality as needed.

**Week 12 (8/14-8/20)**:

- **Final Testing and Documentation**: Perform final tests, finalize documentation, and prepare for release. Ensure comprehensive guides are available for users.

**Week 13 (8/21-8/27)**:

- **Launch and Evaluation**: Deploy the final integration into the Qdrant Web UI. Monitor performance and user feedback. Evaluate the project against initial goals and benchmarks.

**Post-GSoC**:

- **Ongoing Maintenance**: Commit to regular check-ins with the Qdrant community to address any emerging issues or updates.

**Why me**

 currently i am diving into the world of Rust and taking a course on data mining this semester. In this class, we're getting to know different ways to simplify complex data so we can understand it better, different dimension reduction algorithms and their use . This project is a chance for me to really get better at this, to try out what I'm learning in a real project, and to give something back by sharing my work with everyone.
  
I love the way open source works, and participating in open Source activities has introduced me to things I'd never known before, improved my coding skills and met a lot of interesting people who I've enjoyed communicating with, and I hope to contribute more to the open source world. If I'm lucky enough to be selected for this project, I'll take it seriously, keep contributing to the community by continuing to maintain it in the future. Although GSoC may be over, my enthusiasm for open source isn't.
