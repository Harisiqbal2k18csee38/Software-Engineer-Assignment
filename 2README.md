
Multi-language Design Smells: A Backstage Perspective

Mouna Abidi	Moses Openja	Foutse Khomh
École Polytechnique Montréal	École Polytechnique Montréal	École Polytechnique Montréal
Montréal, Canada	Montréal, Canada	Montréal, Canada
mouna.abidi@polymtl.ca	moses.openja@polymtl.ca	foutse.khomh@polymtl.ca
 

ABSTRACT

Context: Multi-language systems became prevalent with techno-logical advances. Developers opt for the combination of program-ming languages to build an application. Problem: Software quality is achieved by following good practices and avoiding bad ones. How-ever, most of the practices in the literature are applied to a single programming language and do not consider the interaction between programming languages. Objective: We previously defined a cat-alog of bad practices i.e., design smells related to multi-language systems. This paper aims to provide empirical evidence on the rele-vance of our catalog and its impact on software quality. Method: We analysed 262 snapshots of nine open source projects to detect occurrences of multi-language design smells. We also extracted information about the developers that contributed to those systems. We plan to perform an open and a closed survey targeting develop-ers in general but also developers that contributed to those systems. We will survey developers about the perceived prevalence of those smells, their severity and impact on software quality attributes.

KEYWORDS

Survey, Multi-language systems, Design smells, JNI

ACM Reference Format:

Mouna Abidi, Moses Openja, and Foutse Khomh. 2020. Multi-language Design Smells: A Backstage Perspective. In 17th International Conference on Mining Software Repositories (MSR ’20), October 5–6, 2020, Seoul, Republic of Korea. ACM, New York, NY, USA, 4 pages. https://doi.org/10.1145/3379597. 3387508
 

in Facebook embedded JavaScript widgets integrated in those web-sites.1 Another example is a bug reported in 2018 in libguests due to misuse of the guideline specification defined when using Java Na-tive Interface (JNI) to combine Java and C++ code.2 Consequently, multi-language systems present additional challenges compared to mono-language systems. Software quality has been studied in the literature and was often related to occurrences of patterns, anti-patterns, and smells [1, 2]. However, most of these studies discussed only patterns and smells in the context of mono-language systems and do not consider the interaction between programming lan-guages. While a design smell may not definitively identify an error, its presence suggests a potential trouble spot, a place where there is an increased risk of a potential future failure. We previously doc-umented a catalog of multi-language design smells, recurrent bad coding or design practice when combining programming languages [3, 4]. We aim through this paper to investigate if our catalog of smells is prevalent. We also aim to investigate its severity and im-pact on software quality attributes. To achieve our objectives, we analysed nine open source projects to detect occurrences of multi-language design smells. We plan to conduct a survey, we believe that a survey is the best method to retrieve developers’ experience and practices when dealing with multi-language systems [5]. We present in the following the proposed methodology to achieve our objectives.

2	STUDY DESIGN

We present in this section our methodology to perform this study.
 

1	INTRODUCTION

Modern applications are moving from the usage of a single program-ming language to build an application, towards the combination of several programming languages. Developers often leverage the strengths and take advantages of several programming languages to cope with the pressure of the market. However, despite the several advantages introduced by the combination of programming lan-guages, it is not without introducing new and additional challenges. Earlier in 2013, famous websites were not accessible due to an issue


Permission to make digital or hard copies of all or part of this work for personal or classroom use is granted without fee provided that copies are not made or distributed for profit or commercial advantage and that copies bear this notice and the full citation on the first page. Copyrights for components of this work owned by others than ACM must be honored. Abstracting with credit is permitted. To copy otherwise, or republish, to post on servers or to redistribute to lists, requires prior specific permission and/or a fee. Request permissions from permissions@acm.org.

MSR ’20, October 5–6, 2020, Seoul, Republic of Korea

©	2020 Association for Computing Machinery. ACM ISBN 978-1-4503-7517-7/20/05. . . $15.00 https://doi.org/10.1145/3379597.3387508
 

2.1	Setting Objectives and Research Questions

We started by setting the objective of our study. Our objectives are to assess the perceived critically of our catalog of multi-language design smells and their prevalence. We chose to carry an empirical study using a survey because development and maintenance are manual activities performed by developers. Thus, the developers’ evaluation is important. We also aim to capture the perceived impact by developers since they are the ones who interact daily with multi-language systems and who suffer from their challenges [2]. The quality focus is source code comprehension and maintainability, which can be negatively impacted by the occurrences of types of design smells. The context of the study consists of (i) objects, i.e., design smells detected in nine open source projects; and (ii) subjects (participants), i.e., professional developers providing their perception of multi-language design smells. Our target subjects of this study are software developers in general but also developers that contributed to the analysed systems.


1	https://www.wired.com/2013/02/facebook-widget-snafu/

2https://bugzilla.redhat.com/show_bug.cgi?id=1536762
 
MSR ’20, October 5–6, 2020, Seoul, Republic of Korea

For that, we started by analysing the code of open source projects to extract occurrences of multi-language design smells in the con-text of JNI systems. Those systems were not part of the definition of design smells but will be used for their validation. We also ex-tracted the information of the developers that contributed to the files impacted by those design smells. We then designed two sur-veys. An open survey targeting professional software developers, but also a closed survey targeting developers that contributed in the smelly files. We defined in previous work 15 distinct types of design smells related to multi-language systems [3, 4]. Those smells are related to the development and design when combining between programming languages. They were identified from mining several sources of information i.e., literature, developers’ blog, bug reports, and open source projects. We aim through this study to assess the prevalence of this catalog from the developers’ perspective. We decided to conduct a survey because we believe that it is the best method to retrieve developers’ experience with multi-language de-sign smells and capture theirs critically. We defined our research questions as follows:

RQ1: Are multi-language design smells commonly faced by developers? We previously documented a catalog of multi-language design smells [3, 4]. We aim through this research question to assess how developers perceive the prevalence of this catalog. We are also interested to investigate if some specific types of smells are perceived to be more prevalent than others. We defined the following null hypothesis: H1: The design smells studied in this paper are not commonly faced by developers.

RQ2: What are the reasons behind introducing multi-language design smells? In order to better support developers in im-proving the quality of multi-language systems, it is important to understand the circumstances under which particular de-sign smells occur. Occurrences of design smells could have been intentionally introduced or a result of poor knowledge about multi-language practices. Thus, we attend to study the rationale behind introducing such smells. Our goal here is to study what kind of reasons could lead to the existence of those smells and under which circumstances developers are more prone to introducing such smells. H2: There are no specific reasons behind the introduction of the studied design smells.

RQ3: What is the perceived impact of those design smells? We attempt to study the perceived impact of multi-language design smells on some software quality attributes. These design smells have been extracted from several sources of information (e.g., developers blogs, literature, bug reports, and source code). They have been discussed to negatively impact the source code. However, these assertions have never been verified. Thus, we aim to investigate how developers concretely perceive the impact of those design smells at different quality attributes level. More specifically, we want to identify which quality attributes are more impacted by these smells than the others. We defined the following null hypothesis: H3: Software quality attributes are not impacted by the studied smells.
 
Abidi et al.

RQ4: What are the design smells that developers perceive as the most harmful? During maintenance activities, devel-opers are interested to identify parts of the code that should be tested in priority or refactored. Hence, we aim to identify design smells that are perceived by developers as the most critical, i.e., making the project more prone to faults or in-crease the maintenance tasks. H4: Developers equally perceive the impact of the studied design smells.

RQ5: Do developers plan to refactor those design smells? De-sign smells are generally associated with a specific set of refactoring strategies to remove them depending on the type of smell. Depending on the development cost, developers may decide to remove or not some specific smells. Therefore, we attempt to investigate to what extent developers would apply such refactoring and if some specific refactoring is more likely to be applied than others. H5: There are no spe-cific refactoring applied by developers to remove occurrences of the studied smells.

2.2	Material and Objects

The objects considered in this study are 15 multi-language design smells identified in nine open source projects downloaded from GitHub. We analysed a total of 262 snapshots. To answer our re-search questions, we have to detect occurrences of those smells in our object system. We reused an approach that was developed under Ptidej Tool3 to allow the detection of those smells. This approach is able to detect occurrences of those smells only in the context of JNI systems (Java and C/C++). Thus, our study will focus only on JNI systems. We previously evaluated this detection approach, measured the recall and precision. To ensure reliability for our sur-veys and mitigate any possible threats related to the recall and-or precision of the detection approach, we will manually validate all the occurrences that will be used in this study when asking devel-opers. Having manual validation ensures enough confidence in the absence of false positives. We will provide a replication folder with all the data and analysis performed in this study.4 We present in table 1 a brief definition of the design smells studied in this paper. More details of those smells are available in our published catalog.

2.3	Participants

The survey described in this paper is a combination of both an open and a closed survey. We will present in the following our method-ology to gather the participants for each of those surveys. We plan to collect participants’ backgrounds and demographic information to deal with the representativeness of the results. We will follow guidelines of sampling methods to build samples that seek to meet the goals of this study to ensure better representativeness. We plan to mitigate threats related to convenience sampling as discussed in previous work [8, 9]. We will also clearly discuss the threats and limitations of our methodology.

•	Open Survey: We will use a convenient sample and ran-domly contact participants that satisfy the criteria of the study. Similar to the previous work, we plan to use LinkedIn7


3	http://www.ptidej.net/tools/
4	https://github.com/ResearchML/RegisteredReport_Perception

7https://www.linkedin.com/
 
Multi-language Design Smells: A Backstage Perspective	MSR ’20, October 5–6, 2020, Seoul, Republic of Korea

	Table 1: Multi-language Design Smells
	
Smells	Definition
Not Handling Exceptions	The exceptions are not handled, developers generally rely on the exceptions provided by the other language. [6, 7].

Assuming Safe Multi-language	A value is returned to the other language without being checked. Thus, the interaction between both languages may not be correctly performed.
Return Values	[6].

Excessive Inter-language Commu-	A wrong partitioning in both languages leads to many calls in a way or the other. It adds complexity, takes more time to run and may indicate
nication	a bad separation of concerns.
Too Much Clustering	The multi-language code is concentrated in a few classes, regardless of their concerns and responsibilities.
Too Much Scattering	Many classes are scarcely used in multi-language communication.
Hard Coding Libraries	When different libraries are needed depending on the operating system, they are not loaded with conditions on the operating system, but for
	instance with a try-catch mechanism, making it hard to know which library has really been loaded.
Local References Abuse	The developer does not manage the memory in the native space properly, and does not release local and global references [6].5

Memory Management Mismatch	Reference types passed from one language to another are not released in a language which does not handle the management of memory
	causing memory leaks.
Not Caching Objects’ Elements	A method is called to retrieve a field every time this field is needed, although the field’s ID or value could have been cached.
Not Securing Libraries	The code loads a foreign library without any security check or restriction privilege.6
Not Using Relative Path	A library is loaded using only the name not the path. It cannot be accessed in the same way from everywhere.
Passing Excessive Objects	A whole object is passed as an argument, although only some of the fields were needed, and it would have been better for the system
	performance to pass only these fields.
Unused Method Declaration	A method is declared in the host language but not implemented in the foreign language.
Unused Method Implementation	A method is declared in the host language and implemented in the foreign language, but never called from the host language.
Unnecessary Parameters	Some arguments of a function are used neither in its body nor in the other language.

 

as a research tool to reach potential participants because it is one of the largest, professional social networks in the world. Similar to previous work we plan to combine different sampling strategies [9]. By convenient sample we consider available developers willing to conduct the survey. We also plan to invite professional developers through LinkedIn and post a call for participation in LinkedIn groups. Since in this study we will present code snippets only for JNI systems, we will target developers having experience with both Java and C/C++ programming languages.

•	Closed Survey: We mined open source projects from GitHub repository to detect occurrences of multi-language design smells but also the information about the developer that contributed to the smelly files from the commit logs. By con-tributed we consider any developer that did a commit on those files. Note that in the closed survey, a developer will only be asked about smells in files he contributed on.
Studies in the literature discussed the Ethics of sampling strate-gies [9] in computer science. This study will be subject to ethical consent request form meeting Polytechnic Montreal ethical and scientific criteria designed to protect human participants.8 Survey responses will be collected anonymously using online forms. The anonymous data will be used solely for research to get insights into developers’ perception of multi-language smells. We will assign IDs to each respondent, all the information that will be collected within the framework of this study will remain strictly confidential.

2.4	Execution Plan

The experimental protocol consists of surveys that participants had to answer through CheckMarket website.9 We combine in this study both open and closed surveys.10 Both surveys start with a preamble that includes the information about the principal investigator, the research team, the ethical rights and responsibilities of the inves-tigators and participants (e.g., policy of the study with respect to


8	https://share.polymtl.ca/alfresco/service/api/node/content/workspace/SpacesStore/ b7fbaa9e-8055-41cc-b016-dac345f6cb97?a=false&guest=true
9https://www.checkmarket.com/
10https://s-ca.chkmkt.com/?e=189517&h=B445656A9769E90&l=en
 

anonymity). They also describe the objective of the study so that participants understand our motivations for this survey and have full information to decide whether or not to answer the survey (or parts thereof). We also provide in those surveys definitions of the concepts and the design smells used in this study. We added references in case any of the participants are interested to know more about this topic. The open survey contains in the first part four closed questions to retrieve background information about the practitioners and their profiles. The survey asks about their work positions, the number of years of working experiences, the domain of activities of their organisations, levels of skills in ten program-ming languages. These languages were reported to be in the top ten list of languages used world-wide.11 Note that we will not include the background information in the closed survey since we are not randomly contacting developers but our target population for the closed survey is original developers that contributed in the object systems.

We will provide in those survey source code snippets and ask about whether or not the presented code contains implementation or design problems. We will also investigate the perceived severity and impact of those smells in software quality attributes. For the quality attributes, we selected the following four attributes dis-cussed by Gamma et al. in their seminal book about design patterns, i.e., expandability, modularity, reusability, and understandability, and three other attributes, i.e., simplicity, learnability, and perfor-mance. We will focus on these quality attributes because of their relevance for design (anti) patterns and smells [1, 2]. Regarding the severity of design smells types, we will follow previous work on the perception of mono-language smells and use a Likert scale [1]. This scale will allow comparing responses of multiple respondents. We are aware that this type of study could reflect a subjective per-ception of the studied problem, and might not fully capture the extent to which the design smell could affect software development activities of multi-language projects.



11	https://spectrum.ieee.org/at-work/innovation/the-2018-top-programming-languages
 
MSR ’20, October 5–6, 2020, Seoul, Republic of Korea	Abidi et al.
 

We will select for each type of smell representative instances to perform the survey. Depending on the type of smells, an instance could be a method, a class, files, or a combination of source code files. We will ask about a single smell at the time and do not present code affected by more than one design smell, since we want to evaluate separately each smell. We will ask the participants to perform the following tasks:

•	In your opinion, does the following code(s) contain any occur-rence of design smell(implementation and-or design problem)? We will also inject in these question code snippets that are not impacted by any of the design smells to limit the bias of this study, i.e., isolate situation in which practitioners may provide arbitrary answers or always indicate existing of design smells.
•	If you answered yes to the previous question, please provide an explanation or specify the design smell(s) involved?

•	(In your opinion,) What is the motivation behind using this specific way of implementation? This question is mainly de-signed for the closed survey to study why developers intro-duce or do not remove occurrences of such design smells. However, we will keep this question in both surveys to cap-ture practitioners’ opinions about the rationale of following that specific way of implementation.
•	Would you apply the following refactoring or would you prefer to keep the initial implementation? please explain
•	How do you evaluate the impact of those design smells in the following software quality attributes?
•	Please rank the following design smells from the harmful to harmless ones

2.5	Analysis Plan

We present in the following our analysis plan to answer the research questions:

For RQ1, following previous work [1], we plan to compute for each design smell from the catalog, the percentage of answers in which the practitioners were able to: (1) identify a design or implementation problem when we asked them to evaluate the code snippet containing a design smell. By identified we consider the situation in which the practitioners selected yes to the question: In your opinion, does the following code contain any occurrence of design smell(implementation and-or design problem)?; (2) Identify the specific smell that was introduced on the code snippet. By identifying we will consider a situation in which the practitioners provide a correct answer to the question: If you answered yes to the previous question, please provide an explanation or specify the design smell(s) involved? The percentage will be computed out of the total number of answers to capture the prevalence of each type of smell from the catalog. We will provide the demographic information to clearly state with the representativeness of the results.

For RQ2, we plan to use a manual approach of text analysis to extract topics from the answers provided by the respondents to the open questions. This research question will consider practitioners answer to the question: What is your motivation behind using this specific way of implementation? We plan to follow the methodology performed by Yamashita and Moonen [10] and use coding tech-niques to analyse the answer to the open question. We will follow
 

a double verification process to ensure that the answers are in the right categories and that there is no losses of information when combining into categories.
For RQ3, we plan to compute for each type of smell and each quality attribute the percentage of answers in which the practition-ers reported an impact of the smell on that quality attribute. We will have for each smell, (i) the list of quality attributes that are perceived to be negatively impacted by each smell, (ii) the list of quality attributes that are not impacted (neutral impact), (iii) the list of quality attributes, if any, that could be positively impacted by those design smells. To answer this research question, we will analyse answers to the quantitative question: How do you evaluate the impact of those design smells in the following software quality attributes? We will use the following scale: Very positive, Positive, Not significant, Negative, Very Negative, and Not applicable.

For RQ4, we plan to exploit practitioners’ answers to the ques-tion: Please rank the following design smells from the harmful to harmless ones. Similar to previous work [10], we will rely on Borda count to answer this research question. Borda count is a rank-order aggregation technique if there are n candidates to rank (i.e., design smells in our situation), the first ranked candidates will receive n points, n-1 for the second-ranked, etc. We will have as output the list of all the design smells ranked from the most harmful ones to harmless ones.

For RQ5, for each design smell, we will propose a refactored solution based on the catalog, we plan in this research question to measure for each smell the percentage of answers in which the prac-titioners answered yes to the question Would you consider using this refactored solution or would you prefer to keep the initial implementa-tion? please explain? We will also aggregate the answers to provide a general overview of the application of refactored solutions.

Since reporting only data and numbers might not be enough to provide empirical evidence of the results, we also plan to apply null-hypothesis analysis tests for the quantitative research questions to report statistically significant results.

REFERENCES

[1]	F. Palomba, G. Bavota, M. Di Penta, R. Oliveto, and A. De Lucia, “Do they really smell bad? a study on developers’ perception of bad code smells,” in 2014 IEEE International Conference on Software Maintenance and Evolution. IEEE, 2014, pp. 101–110.

[2]	F. Khomh and Y.-G. Guéhéneuc, “Do design patterns impact software quality positively?” in Software Maintenance and Reengineering, 2008. CSMR 2008. 12th European Conference on. IEEE, 2008, pp. 274–278.

[3]	A. Mouna, K. Foutse, and Y.-G. Guéhéneuc, “Anti-patterns for multi-language systems,” in 24th European Conference on Pattern Languages of Programs (EuroPLoP ’19), July 3–7, 2019, Irsee, Germany. ACM, 2019.

[4]	A. Mouna, G. Manel, K. Foutse, and G. Yann-Gaël, “Code smells for multi-language systems,” in 24th European Conference on Pattern Languages of Programs (EuroPLoP ’19), July 3–7, 2019, Irsee, Germany. ACM, 2019.

[5]	A. Fink, The survey handbook.  Sage, 2003, vol. 1.
[6]	G. Tan and J. Croft, “An empirical security study of the native code in the jdk,” in Proceedings of the 17th Conference on Security Symposium, ser. SS’08. Berkeley, CA, USA: USENIX Association, 2008, pp. 365–377.

[7]	S. Li and G. Tan, “Finding bugs in exceptional situations of jni programs,” in Proceedings of the 16th ACM Conference on Computer and Communications Security, ser. CCS ’09. New York, NY, USA: ACM, 2009, pp. 442–452.

[8]	F. Gravetter, “Forzano, lab research methods for the behavioral sciences,” 2012.

[9]	S. Baltes and S. Diehl, “Worse than spam: Issues in sampling software develop-ers,” in Proceedings of the 10th ACM/IEEE International Symposium on Empirical Software Engineering and Measurement, 2016, pp. 1–6.
[10]	A. Yamashita and L. Moonen, “Do developers care about code smells? an ex-ploratory survey,” in 2013 20th Working Conference on Reverse Engineering (WCRE). IEEE, 2013, pp. 242–251.
