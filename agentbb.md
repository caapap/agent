# Agent Design Document

## 1. Requirement Background

- **Company Business:** Software Development, IT Services, System Integration
- **Organization Composition:** Project Managers, Operations Support, Implementation Engineers, Operations Engineers
- **Roles and Responsibilities:**
  - **Project Managers:** Responsible for project management, requirements analysis, client communication, and project coordination.
  - **Operations Support:** Responsible for business operations, client management, resource management, and financial management.
  - **Implementation Engineers:** Responsible for implementation, training, and maintenance.
  - **Operations Engineers:** Responsible for system operations, monitoring, and optimization.

## 2. Design Goals

- Enhance work efficiency
- Improve collaboration effectiveness
- Elevate technical capabilities

## 3. Functional Requirements

1. **Capability Classification:**
   - **Basic:** Professional knowledge Q&A, format processing, text extraction
   - **Intermediate:** Document drafting assistance, single file code processing, codebase management, troubleshooting analysis
   - **Advanced:** Multi-file code processing, bug handling, single-domain deep search report generation

2. **Model Classification:**
   - **Basic:** GPT-4o-mini
   - **Intermediate:** Claude-3.7-sonnet
   - **Advanced:** Claude-3.7-sonnet-thinking

## 4. Design Approach

### Node Types
*Difficulty levels are indicated by ⭐*

- Problem Classifier (⭐⭐⭐)
- Task Parallelizer (⭐⭐⭐⭐)
- Automatic Orchestrator (⭐⭐⭐⭐⭐)
- Looper (⭐⭐⭐⭐)
- Professional Knowledge Q&A
- Deep Thinking and Analysis
- Multi-turn Translator
- Text Content Extraction
- Table Processing
- PDF Processing
- Word-to-Markdown Converter
- Code Programming
- Operations Troubleshooting
- Document Drafting Assistance
- Document Upload and Parsing
- Image and Text Recognition and Understanding
- To be determined...

1. **Problem Classifier:**  
   Uses a classifier to categorize issues into various types such as Professional Knowledge Q&A, Deep Thinking and Analysis, Programming and Technical Support, Document Drafting Assistance, Document Upload and Parsing, and Image and Text Recognition and Understanding.
   - **Benefits:**
     - **Task Decomposition:** LLM workflows typically involve multiple tasks (e.g., Q&A, content generation, translation). Classifying issues can break down complex inputs into clear subtasks.
     - **Routing Optimization:** Classification enables routing issues to the most suitable model, tool, or processing workflow, thereby avoiding a one-size-fits-all approach.
     - **Context Understanding:** It assists in identifying the intent and domain of an issue, providing the LLM with clearer context to enhance output quality.
     - **Efficiency Enhancement:** Once classified, the workflow can bypass unnecessary computations by directly invoking specialized modules. For example, mathematical problems can be delegated directly to a math solver rather than processed by a generic LLM.
     - **Accuracy Improvement:** Different types of issues require distinct handling methods. Classification allows for the selection of models or tools best suited for a specific domain, mitigating the limitations of general-purpose LLMs.
     - **Resource Optimization:** Specialized classification models or plugins generally consume less computational resources compared to general-purpose LLMs, reducing overall costs.
     - **Scalability:** A modular classification approach renders the workflow easily expandable—new issue types only require updates to the classifier and corresponding logic.
     - **User Experience:** Rapid and accurate classification delivers responses that better meet user expectations, reducing redundant or irrelevant answers.
     
   - **Implementation Approach:**  
     Employ a routing-mode workflow where the input is classified and directed to dedicated subsequent tasks. This modular approach enables separation of concerns and the development of specialized prompts. Without such a workflow, optimizing one type of input might negatively affect the performance of others. The routing strategy is particularly suitable for complex tasks with clearly distinct categories that can be precisely classified using either LLMs or traditional classification models/algorithms.

2. **Task Parallelizer:**  
   - **Benefits:**
     - **Efficiency Improvement:** Processing multiple tasks simultaneously can significantly reduce total processing time, especially in scenarios requiring rapid responses.
     - **Enhanced Accuracy:** Parallel processing enables the leveraging of complementary strengths from multiple models or tools, balancing false positives and negatives to enhance overall output quality.
     - **Resource Optimization:** It makes more efficient use of computational resources, reducing wait times and increasing system throughput.
     - **Diversity:** Executing the same task multiple times can generate a variety of outputs.
     - **Security Safeguard:** Asynchronous security reviews can be established to bolster safety while ensuring the integrity of core responses.
     
   - **Implementation Approach:**  
     Utilize a parallelization workflow based on task segmentation and a voting mechanism. Segmentation involves dividing a task into multiple subtasks, each handled by a different model. Voting aggregates outputs from these subtasks to select the optimal result.

3. **Automatic Orchestrator:**  
   - **Benefits:**
     - **Flexibility:** Automatic orchestration can greatly reduce overall processing time, particularly in scenarios that demand quick responses.
     - **Dynamism:** By automatically identifying and extracting knowledge assets and performing dynamic classification, it addresses complex situations where the nature of subtasks is unpredictable (e.g., when a single project objective triggers multiple changes, or when unpredictable multi-target scenarios in a knowledge base result in varied outcomes).
     
   - **Implementation Approach:**  
     Adopt a cyclical (loop) workflow that utilizes a bidirectional evaluation-optimization loop to continually refine the quality of outputs (such as multi-turn high-quality literary translations or complex search tasks involving several rounds of analysis). It is crucial to establish clear termination conditions for the loop, possibly through setting an appropriate quality threshold.
