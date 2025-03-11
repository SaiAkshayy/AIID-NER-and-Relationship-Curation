# AI Incident Database: Entity Identification and Relationship Curation

## Introduction:

The AI Incident Database (AIID) is a comprehensive open-source repository documenting real-world incidents where artificial intelligence (AI) systems have caused harm. These incidents often involve three critical roles: developers, deployers, and victims. Understanding the relationships between these roles is essential to identifying systemic risks, enabling governance, and fostering ethical AI practices. However, current methods of identifying and clustering these entities rely heavily on manual processes, which are time-consuming and prone to bias and errors.

This project will automate entity identification and clustering using advanced natural language processing (NLP) and machine learning (ML) techniques. By enhancing the accuracy and efficiency of entity extraction and relationship mapping, the project provides a scalable framework to analyze AI incidents and generate actionable insights.

## Problem Statement:

The manual nature of current entity identification processes introduces inefficiencies and limits the ability to analyze the complex relationships between developers, deployers, and victims. Additionally, these challenges hinder the extraction of structured insights necessary for effective decision-making and governance. Key issues include:

### Resource-intensive curation processes.

- Difficulty in capturing nuanced relationships within dynamic networks.

- Limited ability to derive meaningful insights due to unstructured data.

This project addresses these issues by leveraging automated methods to streamline analysis while enhancing data quality and interpretability.

## Methodology:

### Data Pipeline:

The primary data source was the AI Incident Database, which consists of three main collections:

- Reports Collection: Contains 3,921 indexed reports with detailed descriptions and metadata.

- Entities Collection: Includes 2,388 unique entities categorized into developers, deployers, and victims.

- Incidents Collection: Documents 793 distinct incidents, each linked to multiple reports for contextual depth.

Preprocessing involved standardizing and validating textual data to ensure uniformity and readiness for analysis. MongoDB was used for storage, enabling efficient querying and compatibility with unstructured data.

### Entity Recognition:

A fine-tuned RoBERTa transformer model was employed for Named Entity Recognition (NER). The process entailed tokenizing raw text into manageable units, embedding tokens into high-dimensional semantic spaces, and tagging entities. Despite its strengths, the model encountered challenges in identifying abstract entities like "pedestrian" or ambiguous roles, which led to misclassification.

### Entity Clustering:

Text embeddings generated using the all-MiniLM-L6-v2 model provided a semantic representation of entities. These embeddings were clustered using K-Means (set to 100 clusters), enabling the identification of patterns and relationships among entities. This structured clustering process uncovered themes such as recurring developer-victim interactions and deployer-specific risks. Cluster labels were manually generated.

<img src= "https://github.com/user-attachments/assets/ed6ee00e-c4ca-4287-93ba-bf552344cc89" width="700" height="500">

### Relationship Mapping:

Entity relationships were visualized using network graphs created with PyViz and NetworkX. The graphs illustrated connections between developers, deployers, and victims, highlighting relationships such as harm caused by developers or deployers of the AI Systems.

<img src="https://github.com/user-attachments/assets/d334f23d-5ee9-40a8-9709-9888319f2010" alt="Screenshot 2024-12-05 222914" width="500" height="350">


## Results and Insights:

### Enhanced Entity Identification:

Automated NER significantly improved the efficiency of identifying developers, deployers, and victims within incident reports. This automation reduced reliance on manual curation and improved the precision of extracted entities by incorporating semantic context.

### Clustering Insights:

Clustering revealed actionable patterns and relationships within the data. For example, entities were grouped into meaningful clusters based on their semantic similarity, enabling deeper analysis of developer-deployer-victim interactions. The clustering also highlighted recurring themes, such as incidents involving autonomous vehicles and biased content moderation.

### Visualization of Relationships:

Network graphs provided a comprehensive view of the interconnections between roles. Subgraphs focusing on specific entities, such as Tesla or Facebook, showcased risks and systemic issues unique to these organizations. These visualizations were instrumental in uncovering patterns of harm, responsibility, and governance gaps.

<img src="https://github.com/user-attachments/assets/cd65533a-934f-4143-9ce2-05c11d399662" width="700" height="500">

### Closer look at Tesla and Facebook's Subgraph:

<img src = "https://github.com/user-attachments/assets/ac6ce32e-1692-4d43-98b8-55a70c5f9785" width="500" height="400">  <img src = "https://github.com/user-attachments/assets/105db89a-aca4-44f5-b946-601c39bd6237" width="500" height="400"> 

Tesla’s subgraph illustrates the risks associated with autonomous AI systems, particularly self-driving cars. Victims include accident victims, pedestrians, and engineers, reflecting the consequences of deploying AI without adequate safeguards. Tesla’s graph underscores the importance of safety protocols and regulatory oversight, highlighting the potential for significant harm in autonomous systems.

Facebook's subgraph dives deeper into specific cases. Showing various groups affected by AI systems deployed by Facebook, such as minority groups, child users, and Instagram users. Highlights how Facebook’s AI systems impact diverse users, including vulnerable populations (e.g., children, minority groups). Raises concerns about moderation, privacy, and algorithmic biases affecting these groups.

## Recommendations:

- Improved Entity Extraction Models: Future iterations should integrate context-aware models like GPT-4 to enhance accuracy in identifying ambiguous or abstract entities.

- Enhanced Clustering Techniques: Incorporate additional features such as temporal and geospatial data to refine clustering and uncover latent trends.

- Scalable Infrastructure: Utilize cloud-based solutions (e.g., AWS) to address computational bottlenecks and enable real-time processing.

- Interactive Dashboards: Develop a dynamic interface to visualize entity relationships and provide stakeholders with actionable insights in real-time.

## Limitations:

- Data Quality: Manually curated incident descriptions introduced biases and ambiguities, affecting the reliability of entity extraction.

- Computational Constraints: High resource requirements for large language models (LLMs) posed scalability challenges.

- Model Performance: While effective, the NER model occasionally struggled with nuanced or overlapping roles, necessitating further refinement.

## Future Directions:

Future work will focus on incorporating real-time entity extraction and relationship mapping to provide continuous updates on evolving AI incidents. Expanding graph-based visualizations and integrating temporal data will enable longitudinal studies of trends and systemic risks. Additionally, enhanced dashboards will empower stakeholders to interact with the data dynamically, fostering more effective decision-making.

