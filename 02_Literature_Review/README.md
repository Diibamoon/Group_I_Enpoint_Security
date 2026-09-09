**2.1 Introduction**

This chapter presents a critical review of previous studies related to behavioural detection of file-encrypting ransomware on Windows endpoints using machine learning. The purpose of this literature review is to analyse existing approaches, identify their strengths and limitations, and establish the research foundation for the proposed study.
Based on the reviewed literature, previous studies can be classified into two major categories: traditional behavioural analysis approaches and intelligent and adaptive detection approaches. These classifications provide a general understanding of how researchers have approached ransomware detection before examining specific research themes.

**2.1.1 Behavioural Analysis-Based Detection**

Behavioural monitoring approaches analyse ransomware based on activities performed during execution rather than relying on static signatures. These approaches collect information from operating system interactions, process execution and system-level events. Studies under this category demonstrate that ransomware produces observable behavioural patterns, which can be used as detection indicators. Another classification of behavioural detection focuses on changes produced by ransomware during file encryption. Researchers analyse abnormal file-writing patterns, entropy variation and file integrity changes to identify suspicious encryption activities.

**2.1.2 Intelligent Detection and Response-Based Approaches**

Machine-learning-based ransomware detection approaches have gained attention because they can identify complex relationships between multiple behavioural features. Instead of relying on manually created rules, these methods learn patterns from existing ransomware and benign samples. Recent studies have also focused on real-time endpoint protection by integrating behavioural monitoring with EDR technologies. These approaches aim to provide rapid detection and response while maintaining visibility against ransomware attempting to bypass security mechanisms.

**2.2 Literature Review Format** 
**2.2.1 Windows API Call and System Monitoring**

Windows API calls provide information about how processes interact with the operating system during execution. Analysing the sequence of API calls can reveal malicious behavioural patterns that may not be visible through static malware signatures.

Abdelwahed et al. (2023) developed MalpMiner, which applies Answer Set Programming to dynamic API-call sequences. The approach provided interpretable malware classification because suspicious behaviour could be linked to specific runtime activities. However, its effectiveness depends on the completeness of predefined behavioural rules.

Mokoma and Singh (2025) proposed RanViz, which represents API-call sequences as chronological time-series information. The approach demonstrated that the order and repetition of API activities can help distinguish ransomware behaviour from normal system activities.

Meena and Prabha (2025) investigated zero-shot learning using API-call sequences. Their approach was designed to identify previously unseen malware families without requiring samples from every malware family during training.

Ramamoorthi et al. (2026) used Microsoft Sysmon to collect process and file-system activity in real time. Their framework streamed telemetry to a detection engine and reported malicious process termination in less than 3.2 seconds.

Overall, API-based monitoring provides valuable information about runtime behaviour. However, high-volume Windows telemetry can generate substantial background noise, while attackers may alter API sequences or execution timing to avoid behavioural detection. 

**2.2.2 File-System Activity and Entropy Analysis**

File-system monitoring is directly relevant to ransomware because file-encrypting ransomware modifies large numbers of files during an attack. Researchers commonly examine file-writing behaviour, entropy changes, file extensions and recovery-related activities.
Lee and Lee (2022) demonstrated an important weakness in entropy-based ransomware detection. Their study showed that encoding techniques such as Base32 and Base64 could alter ciphertext entropy and potentially bypass simple entropy thresholds.

Sai et al. (2026) developed a ransomware-detection method using Windows file-system filters and entropy analysis. Suspicious processes could be detected when multiple file writes produced unusually high entropy values.

Ahmed R et al. (2026) combined entropy measurements with file-write velocity using sliding-window analysis. This approach was intended to reduce false positives from legitimate activities such as compression and high-volume file operations.

Amoruso et al. (2026) proposed spot-entropy sampling rather than continuously analysing complete files. Their technique reduced computational requirements while still providing information about suspicious encryption activity.

Hou et al. (2024) analysed 7,796 Windows ransomware samples and reported that 89.97% attempted to delete Windows Volume Shadow Copies. This indicates that recovery-tampering activities can provide additional ransomware indicators beyond file encryption itself. 
These studies demonstrate that entropy and file-system behaviour are useful ransomware indicators. However, entropy should not be used alone because legitimate applications may also create high-entropy files and ransomware can manipulate its encryption behaviour.

**2.2.3 Machine Learning-Based Ransomware Detection**

Machine-learning techniques can analyse multiple ransomware characteristics simultaneously and classify activities as malicious or benign. Most coommonly evaluated algorithms include Random Forest, XGBoost, Support Vector Machine, Logistic Regression and Neural Networks. 
Elsersy et al. compared Random Forest, Neural Network and Logistic Regression. Random Forest achieved approximately 98.1% accuracy, although the dataset did not fully represent runtime ransomware behaviour.

Aljabri et al. (2024) evaluated several machine-learning algorithms using Windows memory dumps. XGBoost achieved approximately 97.85% accuracy with a false-positive rate of around 2%, although memory acquisition introduces additional resource requirements.

Singh and Singh (2024) found that XGBoost achieved the highest ROC-AUC of 0.989, while Random Forest obtained the highest F1-score of 0.976. Their results demonstrate that model performance should not be evaluated using accuracy alone.

Muppidi and Sureshkumar (2025) proposed an optimised XGBoost behavioural approach that reported 98.5% accuracy, 98.2% F1-score and 1.2% false-positive rate. However, the evaluation relied on synthetic ransomware samples, limiting conclusions about real-world performance.

Panja et al. (2025) used feature-selection techniques with Random Forest and reported approximately 99.39% accuracy with relatively low resource usage. Nevertheless, dependence on predefined features may reduce adaptability to previously unseen malware.

Overall, Random Forest and XGBoost frequently produced strong results, but no algorithm can be considered universally superior. Performance varies according to dataset characteristics, selected features and experimental conditions. 

**2.4.4 Real-Time Detection, EDR and Evasion**

Real-time ransomware detection and Endpoint Detection and Response (EDR) approaches focus on continuously monitoring endpoint activities and identifying malicious behaviour before significant damage occurs. Unlike traditional detection methods that rely on previously known malware signatures, these approaches analyse runtime behaviour, telemetry information and suspicious execution patterns.

Abdelwahed et al. (2023) proposed MalpMiner, a dynamic malware-analysis approach that analyses API-call behaviour using Answer Set Programming. The study demonstrated that runtime behavioural information can improve malware detection while maintaining interpretability. However, the approach depends on predefined behavioural rules, which may reduce effectiveness against new execution patterns.

Hussain et al. (2024) reviewed hybrid malware detection approaches combining static and dynamic analysis. The study highlighted that combining multiple sources of information can improve detection capability, although hybrid deep-learning approaches may require significant computational resources.

Mokoma and Singh (2024) investigated API-call sequence analysis for ransomware detection. Their work showed that temporal behavioural information can provide useful indicators for identifying ransomware execution patterns. However, behavioural monitoring approaches may still face challenges when attackers modify their execution behaviour.

Marcinkowski et al. (2024) proposed MIRAD, an interpretable ransomware attack detection approach. The study focused on improving transparency in machine-learning-based ransomware detection by providing explanations for classification decisions. However, explainable approaches may introduce additional computational overhead.

Meena and Prabha (2025) explored zero-shot learning using API-call sequences to improve detection of previously unseen malware families. This approach is important because ransomware variants continue to evolve and may not appear in existing training datasets.
Manthena et al. (2025) reviewed Explainable Artificial Intelligence (XAI) techniques for malware analysis. The study highlighted the importance of interpretable security models but identified that practical XAI benchmarking for Windows environments remains limited.

Fang and Saadawi (2026) investigated hybrid AI-based behavioural monitoring approaches for improving real-time ransomware detection. Their work represents the growing trend towards combining multiple behavioural indicators rather than relying on a single detection feature.

Overall, this demonstrates that modern ransomware detection is moving towards real-time, hybrid and explainable approaches. However, challenges remain regarding computational cost, limited real-world validation and the ability to maintain detection capability against evolving ransomware evasion techniques.

