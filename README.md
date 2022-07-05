# Cloud Provider (Nubiz)

## Background
Profiling is a process of dynamic program analysis that measures Memory and CPU usage during the runtime. Most commonly, profiling information servers to aid program optimizations.  For example, one of the most known JVM profilers is JProfiler. JProfiler collects the following data: methods calls data(aka CPU profiling), allocations (heap allocations, GC), threads and locks, higher level subsystems like JDBC, HTTP, etc. Two main components of JProfiler are JProfiler UI and JProfiler agent.
<table width="256px">
  <tr>
    <td><img src="./images/jprofiler.png"/></td>
  </tr>
  <tr><td align="center">JProfiler</td></tr>
</table>  

Jprofiler agent uses the JVM tool interface. JVMTI is a native interface that a profiler uses to gain access to information and add hooks for inserting its own instrumentation. This means that at least part of the profiling agent must be implemented as native code and so a JVM profiler is not platform independent. To load the agent at startup, a VM parameter [-agentpath:] is added to the command line. Once loaded, the profiling agent tasks the JVMTI to be notified of all kinds of events, such as thread creation or class loading. Some of these events directly deliver profiling data. Using the class loading event, the profiling agent instruments classes as they are loaded and inserts its own byte-code to perform its measurements. The JProfiler agent only collects the profiling data. The JProfiler UI is started separately and connects to the profiling agent through a socket. This means that it is actually irrelevant if the profiled JVM is running on the local machine or on a remote machine - the communication mechanism between the profiling agent and the JProfiler UI is always the same. JProfiler can work in two modes: on start and attach. In attach mode the JProfiler agent is loaded on the fly and is limited, because some features are not available in later phases of JVM lifecycle (see JVMTI specs).


## Problem Statement

## Facts and Observation

## Solution
