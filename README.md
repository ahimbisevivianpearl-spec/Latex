# Latex
Latex

\documentclass[12pt,a4paper]{article}

% ---------------- PACKAGES ----------------
\usepackage[a4paper,margin=1in]{geometry}
\usepackage{times}
\usepackage{setspace}
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage{array}
\usepackage{enumitem}
\usepackage[hidelinks]{hyperref}
\usepackage{float}
\usepackage{titlesec}

% ---------------- FORMATTING ----------------
\onehalfspacing
\setlength{\parindent}{0.5in}
\setlength{\parskip}{4pt}
\setcounter{secnumdepth}{3}
\setcounter{tocdepth}{2}

\titleformat{\section}
  {\normalfont\bfseries\large}{\thesection.}{0.5em}{}
\titleformat{\subsection}
  {\normalfont\bfseries\normalsize}{\thesubsection}{0.5em}{}

\begin{document}

% ==================================================
% TITLE PAGE
% ==================================================
\begin{titlepage}
\begin{center}

{\Large\textbf{UGANDA CHRISTIAN UNIVERSITY}}\\[0.5cm]

{\large FACULTY OF [INSERT YOUR FACULTY]}\\[1cm]

{\large\textbf{ICT1102: ESSENTIAL HARDWARE AND SOFTWARE CONCEPTS}}\\[1cm]

{\Large\textbf{INDIVIDUAL TECHNICAL RESEARCH AND APPLIED COMPUTING REPORT}}\\[0.8cm]

\textbf{CASE STUDY TITLE}\\[0.3cm]

{\large Windows Performance Monitoring and Administrative
Diagnostics: Diagnosing Slow Startup and Repeated Application
Failures in Windows}\\[1.5cm]

\begin{flushleft}
\textbf{GROUP NUMBER:} 16\\[0.4cm]
\textbf{STUDENT NAME:} Ahimbise Vivian Pearl\\[0.4cm]
\textbf{REGISTRATION NUMBER:} M26B13/002\\[0.4cm]
\textbf{SEMESTER:} Advent 2026\\[0.4cm]
\textbf{DATE OF SUBMISSION:} [Insert date]
\end{flushleft}

\vfill
\end{center}
\end{titlepage}

\pagenumbering{roman}

% ==================================================
% ABSTRACT
% ==================================================
\section*{Abstract}
\addcontentsline{toc}{section}{Abstract}

Computer performance is important in education, business and
everyday life because it affects how quickly users can start
computers, open applications and complete tasks. Windows computers
may sometimes experience slow startup, delayed application
responses and repeated application failures. These problems may
result from high resource usage, background processes, startup
applications or software errors, and do not always require hardware
replacement. This report examines the use of Windows diagnostic
tools to investigate slow startup and repeated application failures.
It focuses on Task Manager, Event Viewer and Startup Apps, while
discussing Performance Monitor, Windows event identifiers and
performance baselines. Task Manager provides information about CPU,
memory and disk utilization; Event Viewer records application and
system events; and Startup Apps helps users review programs that
launch automatically. The report adopts a practical diagnostic
approach supported by Microsoft technical documentation and a
university-library book on computer and drive performance. It
explains the importance of interpreting observations in context,
comparing readings over time and making evidence-based
troubleshooting decisions. The reliability of the conclusions
depends on the actual readings and event records collected during
the investigation.

\newpage
\tableofcontents
\newpage

\pagenumbering{arabic}

% ==================================================
% 1. INTRODUCTION
% ==================================================
\section{Introduction}

Computers are important tools in education, business and everyday
life. They help users perform tasks such as preparing documents,
conducting research, communicating and managing information. For a
computer to work effectively, its hardware and software must
operate properly. However, Windows computers may sometimes become
slow during startup, take a long time to open applications or
experience repeated application failures.

These problems can affect productivity and make it difficult for
users to complete their work. Some users may assume that a slow
computer needs more memory or a new hard drive. However, replacing
hardware without first identifying the cause can lead to unnecessary
expenses. Performance problems may also be related to background
processes, startup applications, software errors or high system
resource usage.

Windows provides diagnostic tools that help users investigate these
problems. Task Manager displays information about running processes
and the use of CPU, memory and disk resources. Event Viewer records
application and system events that can help identify errors.
Performance Monitor provides additional information about computer
performance over time.

This report examines how these tools can be used to investigate slow
startup and repeated application failures. It also discusses Windows
event identifiers and performance baselines, which help
administrators interpret diagnostic information and compare
performance against normal operating conditions.

\subsection{Problem Statement}

Some Windows users experience slow computer startup, delayed
application responses and applications that occasionally stop
working or produce errors. Without proper diagnosis, it may be
difficult to determine whether these problems are caused by high
resource usage, software issues, startup programs or other system
conditions. Making changes without sufficient evidence may fail to
solve the problem or introduce additional difficulties. Therefore,
there is a need to use Windows diagnostic and performance monitoring
tools to collect evidence, identify possible causes and recommend
appropriate troubleshooting actions before considering hardware
replacement.

\subsection{Research Objectives}

The objectives of this report are:

\begin{enumerate}[label=\arabic*.]
    \item To examine CPU, memory and disk utilization using Task Manager.
    \item To investigate recorded application errors using Event Viewer.
    \item To review applications configured to start automatically.
    \item To explain the importance of event identifiers and performance baselines.
    \item To recommend evidence-based approaches to Windows troubleshooting.
\end{enumerate}

% ==================================================
% 2. RESEARCH SOURCES AND LITERATURE REVIEW
% ==================================================
\section{Research Sources and Literature Review}

\subsection{University Library Book}

The book consulted for this report is Peter Norton's
\textit{Introduction to Computers}, sixth edition. The relevant
section is ``Measuring and Improving Drive Performance,'' pages
247--252. The section discusses drive performance, average access
time, data transfer rate and methods of improving disk performance
\cite{norton}.

The book provides a foundation for understanding why storage
performance matters when investigating a slow computer. Disk
activity can affect how quickly applications and files load.
However, disk performance should not be considered in isolation
because CPU usage, memory pressure, startup applications and
software errors may also affect responsiveness.

\subsection{Library Research Record}

\begin{table}[H]
\centering
\caption{University library research record}
\begin{tabular}{p{4cm}p{9cm}}
\toprule
\textbf{Item} & \textbf{Details} \\
\midrule
Book title & Introduction to Computers \\
Author & Peter Norton \\
Edition & Sixth edition \\
Chapter/section & Measuring and Improving Drive Performance \\
Pages consulted & 247--252 \\
Catalogue/call number & 004 NOR \\
Publisher website listed in group presentation &
\url{http://www.mhhe.com/peternorton} \\
\bottomrule
\end{tabular}
\end{table}

\subsection{Task Manager}

Task Manager provides information about running processes and
resource utilization. It can help users identify processes that
consume significant CPU, memory or disk resources. Microsoft
documentation explains how Task Manager can support process
troubleshooting \cite{taskmanager}. A high reading should still be
interpreted in context because utilization changes with workload.

\subsection{Event Viewer and Event Identifiers}

Event Viewer records events produced by Windows and applications.
The records can help users investigate application failures and
system problems. Event identifiers help distinguish event types,
but an event should be interpreted using its source, description,
timing and context rather than assuming that every error caused the
reported performance problem \cite{events}.

\subsection{Performance Monitor and Baselines}

Performance Monitor can collect performance measurements over time.
A performance baseline describes normal system behaviour and
provides a point of comparison when later problems occur.
Microsoft's performance troubleshooting guidance supports systematic
investigation of possible bottlenecks \cite{performance,perfmon}.

\subsection{Startup Applications}

Applications configured to start automatically may increase the
workload during startup. Reviewing startup applications can help
users identify unnecessary programs. However, applications should
only be disabled when their purpose is understood and the change
is safe \cite{startup,microsofttips}.

The sources complement one another. The library book provides
background on storage performance, while Microsoft documentation
explains how Windows tools can be used to investigate resource
usage, events and startup applications.

% ==================================================
% 3. METHODOLOGY AND PRACTICAL INVESTIGATION
% ==================================================
\section{Methodology and Practical Investigation}

\subsection{Research Approach}

This study used a practical diagnostic approach to investigate
Windows computer performance. The investigation involved examining
system resources, reviewing recorded application events and
checking applications that start automatically when the computer
is switched on. Microsoft documentation and the university-library
book were also consulted to understand the tools and concepts used
in the investigation.

\subsection{Tools Used}

The following Windows tools were selected:

\begin{enumerate}[label=\arabic*.]
    \item \textbf{Task Manager:} Used to examine CPU, memory and
    disk utilization and identify applications using significant
    system resources.

    \item \textbf{Event Viewer:} Used to review Windows application
    logs and identify recorded errors or critical events.

    \item \textbf{Startup Apps:} Used to examine applications
    configured to start automatically and their reported startup
    impact.

    \item \textbf{Performance Monitor:} Identified as an additional
    tool for monitoring computer performance over time.
\end{enumerate}

\subsection{Procedure}

First, Task Manager was opened to examine the computer's resource
utilization. The CPU, memory and disk readings were to be observed
and recorded.

Second, Event Viewer was opened and the Windows Application log
was examined for entries marked Error or Critical. Where available,
the event source and event identifier were noted.

Third, the Startup Apps section in Task Manager was examined to
identify enabled applications and their reported startup impact.

Finally, the observations were considered alongside Microsoft
documentation and the library reference to determine how the tools
can support troubleshooting. No changes to system settings were
assumed unless they were actually performed and observed.

\subsection{Ethical and Practical Considerations}

The investigation was limited to the researcher's own computer and
normal diagnostic tools. Existing event records were viewed without
deleting them. Any proposed changes to startup applications or
system settings should be authorized, reversible and evaluated
before being recommended.

% ==================================================
% 4. RESULTS AND FINDINGS
% ==================================================
\section{Results and Findings}

\subsection{Task Manager Observations}

Task Manager was used to examine the computer's CPU, memory and
disk utilization. The readings should be recorded at the time of
observation because resource utilization changes as applications
open and close.

\begin{table}[H]
\centering
\caption{Task Manager resource observations}
\begin{tabular}{p{4cm}p{3cm}p{6cm}}
\toprule
\textbf{Resource} & \textbf{Observed reading} &
\textbf{Comments} \\
\midrule
CPU utilization & [Enter actual reading] &
[Describe what was observed] \\
Memory utilization & [Enter actual reading] &
[Describe what was observed] \\
Disk utilization & [Enter actual reading] &
[Describe what was observed] \\
\bottomrule
\end{tabular}
\end{table}

These readings provide a snapshot of resource use. A high reading
may indicate that a resource is busy at that moment, but a single
reading is not sufficient to prove the cause of slow performance.

\subsection{Event Viewer Findings}

The Windows Application log was examined for recorded application
errors and critical events. The relevant details should be entered
in the table below from the actual computer.

\begin{table}[H]
\centering
\caption{Event Viewer observations}
\begin{tabular}{p{2.5cm}p{2.5cm}p{2cm}p{5.5cm}}
\toprule
\textbf{Log} & \textbf{Source} & \textbf{Event ID} &
\textbf{Observed description} \\
\midrule
[Enter log] & [Enter source] & [Enter ID] &
[Enter actual description] \\
\bottomrule
\end{tabular}
\end{table}

If no relevant error or critical event was found, this should be
reported accurately. Event identifiers help distinguish different
types of recorded events. However, an event should be interpreted
using its description, context and timing rather than assuming that
every error caused the computer's performance problem.

\subsection{Startup Applications Findings}

The Startup Apps section was examined to identify applications
configured to launch automatically.

\begin{table}[H]
\centering
\caption{Startup application observations}
\begin{tabular}{p{4cm}p{3cm}p{5cm}}
\toprule
\textbf{Application} & \textbf{Startup impact} &
\textbf{Observed status or action} \\
\midrule
[Enter application] & [Enter impact] &
[Enter actual status] \\
\bottomrule
\end{tabular}
\end{table}

Applications with high startup impact may contribute to a slower
startup experience. Nevertheless, the reported impact does not by
itself prove that an application is responsible for every startup
delay.

\subsection{Performance Baseline}

A performance baseline is a record of normal system performance
that can be used as a point of comparison when investigating later
problems. The CPU, memory and disk readings collected during this
investigation can provide an initial snapshot, but repeated
measurements under comparable conditions would be needed to
establish a more reliable baseline.

No improvement after a system change should be claimed unless
before-and-after measurements were actually collected.

% ==================================================
% 5. DISCUSSION AND ANALYSIS
% ==================================================
\section{Discussion and Analysis}

The practical investigation demonstrates how Windows diagnostic
tools provide different types of evidence. Task Manager presents
a current view of resource utilization, while Event Viewer provides
records of application and system events. Startup Apps helps
identify applications configured to run when Windows starts.

These tools complement one another. For example, high disk
utilization may suggest that storage activity should be investigated,
while repeated application errors may require examination of the
relevant event details. Neither observation alone establishes the
complete cause of a problem.

Event identifiers are useful because they help users locate and
distinguish specific events. Performance baselines are equally
important because they allow current readings to be compared with
previously observed normal behaviour. Together, these concepts
encourage evidence-based troubleshooting instead of relying on
assumptions.

A limitation of this investigation is that resource readings
represent conditions at a particular time. Results may differ
depending on running applications, background activity and the
state of the computer. A longer investigation using repeated
measurements and Performance Monitor could provide stronger
evidence.

% ==================================================
% 6. RECOMMENDATIONS
% ==================================================
\section{Recommendations}

Based on the diagnostic approach and technical literature, the
following recommendations are made:

\begin{enumerate}[label=\arabic*.]
    \item Use Task Manager to identify applications or processes
    that consistently consume significant CPU, memory or disk
    resources.

    \item Review Event Viewer messages and event identifiers when
    applications repeatedly fail.

    \item Review startup applications and consider disabling only
    unnecessary applications whose purpose is understood and whose
    removal from startup is safe.

    \item Record resource utilization under comparable conditions
    to establish a more useful performance baseline.

    \item Use Performance Monitor when more detailed or continuous
    measurements are required.

    \item Avoid replacing computer hardware before collecting
    evidence and investigating possible software-related causes.

    \item Repeat diagnostic checks after any authorized change to
    determine whether performance has actually improved.
\end{enumerate}

% ==================================================
% 7. CONCLUSION
% ==================================================
\section{Conclusion}

Windows performance problems such as slow startup and repeated
application failures should be investigated systematically.
Task Manager, Event Viewer and Startup Apps provide useful
evidence about resource utilization, recorded errors and
applications that launch automatically. Event identifiers support
the interpretation of specific events, while performance baselines
provide a point of comparison for later measurements.

The investigation also shows that a single reading or error
message may not fully explain a computer problem. Reliable
conclusions require observations to be interpreted in context and,
where possible, compared over time. Using these tools carefully
can help users identify possible causes, make informed
troubleshooting decisions and avoid unnecessary changes or
hardware replacement.

% ==================================================
% 8. INDIVIDUAL CONTRIBUTION AND AI ASSISTANCE
% ==================================================
\section{Individual Contribution and AI Assistance}

\subsection{Individual Contribution}

The student should describe the work personally completed,
including the diagnostic checks conducted, sources consulted,
observations recorded and analysis performed. This section should
be edited to reflect the student's actual contribution.

\subsection{AI Assistance Statement}

If AI tools were used, their actual role should be described in
accordance with the lecturer's instructions and university
requirements. The student remains responsible for verifying
references, checking technical claims and ensuring that the
reported observations represent work actually conducted.

% ==================================================
% REFERENCES
% ==================================================
\newpage
\begin{thebibliography}{9}
\addcontentsline{toc}{section}{References}

\bibitem{norton}
P. Norton, \textit{Introduction to Computers}, 6th ed.,
section ``Measuring and Improving Drive Performance,''
pp. 247--252. Catalogue/call number: 004 NOR.
Verify the remaining publication details against the library copy
consulted.

\bibitem{taskmanager}
Microsoft, ``Troubleshoot processes by using Task Manager,''
Microsoft Learn. [Online]. Available:
\url{https://learn.microsoft.com/en-us/troubleshoot/windows-server/support-tools/support-tools-task-manager}

\bibitem{performance}
Microsoft, ``Troubleshoot performance problems in Windows,''
Microsoft Learn. [Online]. Available:
\url{https://learn.microsoft.com/en-us/troubleshoot/windows-server/performance/troubleshoot-performance-problems-in-windows}

\bibitem{perfmon}
Microsoft, ``Troubleshoot issues using Performance Monitor,''
Microsoft Learn. [Online]. Available:
\url{https://learn.microsoft.com/en-us/troubleshoot/windows-server/support-tools/troubleshoot-issues-performance-monitor}

\bibitem{events}
Microsoft, ``Appendix L -- Events to Monitor,''
Microsoft Learn. [Online]. Available:
\url{https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/appendix-l--events-to-monitor}

\bibitem{startup}
Microsoft, ``Configure Startup applications in Windows,''
Microsoft Support. [Online]. Available:
\url{https://support.microsoft.com/en-gb/windows/experience/startup-boot/configure-startup-applications-in-windows}

\bibitem{microsofttips}
Microsoft, ``Tips to improve PC performance in Windows,''
Microsoft Support. [Online]. Available:
\url{https://support.microsoft.com/en-gb/windows/experience/performance-optimization/tips-to-improve-pc-performance-in-windows}

\end{thebibliography}

\end{document}
