+++
date = "2017-08-22"
title = "Migrating between EFM32 parts in Simplicity Studio "
author = "Paul Gardner-Stephen"
+++

<div class="post-body entry-content" id="post-body-9157724804819240516" itemprop="description articleBody">
One of our projects at the moment involves the EFM32 Pearl Gecko low-power microcontroller.  These are really nice, and capable of very low power consumption.<br/>
<br/>
At the last minute, our supplier could only source us the Jade Gecko instead of Pearl Gecko chips. The only difference is the lack of FPU, so far as I know. Our project doesn't do any floating point, so there wasn't a problem there, or at least, so I thought.<br/>
<br/>
However, when I tried to change the part in Simplicity Studio I hit endless problems, largely due to a lack of understanding about how Simplicity Studio works.<br/>
<br/>
Because we were basing our project on a standard kit board, and had made our PCB pin-compatible, we were continuing to use the Board Support Package (BSP) for that kit. The new part, however, was not an option in that kit, so I had to tell Simplicity Studio that I was not using that kit anymore.  This was the source of all my pain, but it took me several hours of frustration to figure that out.  This is because the error messages that were being generated were not particularly helpful. <br/>
<br/>
It would complain about strange missing include files, like <span>redirectserialconfig.h</span> during the build process. This makes sense as I now understand that such files are provided by the BSP -- although the particular magic by which it provides them I still don't fully understand.<br/>
<br/>
This was because those files are provided from kit-specific include directories.<br/>
<br/>
This meant I was faced with either: (1) keeping the kit, and having the wrong MCU set, which might or might not work through binary compatibility, or (2) having to build a BSP myself, which I really wanted to avoid, as I still don't have enough low-level understanding of what is going on.<br/>
<br/>
A bit of digging around and I discovered that the properties dialog of Simplicity studio which lets you choose among the supported parts on a given kit in reality just sets some #defines and include directories.  Thus, all I needed was:<br/>
<br/>
1.  Go into Properties -&gt; C/C++ Build -&gt; Settings and for each build target modify GNU ARM C Compiler -&gt; Symbols do delete the <span>EFM32PG1B200F256GM48=1</span> line, and replace it with <span>EFM32JG1B200F256GM48=1 </span><span>(your part names may naturally be different)</span><br/>
<br/>
2. Go into Properties -&gt; C/C++ Build -&gt; Settings and for each build target modify GNU ARM C Compiler -&gt; Includes and change  <span>"${StudioSdkPath}/Device/SiliconLabs/EFM32PG1B/Include"</span> to <span>"${StudioSdkPath}/Device/SiliconLabs/EFM32JG1B/Include"</span> (again, adjust part families according to your project).<br/>
<br/>
Then, finally, I could get the build to succeed again.  This is probably all well known to just about everyone, but it tripped me up, so I figured I would document it in case it was useful for others (and also so that I can remember better how to do it in the future).<br/>
<br/>
For those like myself who are more command-line oriented, here is the diff for my project (which unfortunately I cannot share the complete thing with you):<br/>
<br/>
<span>diff --git a/.cproject b/.cproject</span><br/>
<span>index 75fdb6d..7ed84db 100644</span><br/>
<span><span>--- </span><span>a/.cproject</span></span><br/>
<span><span>+++ </span><span>b/.cproject</span></span><br/>
<span>@@ -35,7 +35,7 @@</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.def.symbols.56412088" name="Defined symbols (-D)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.def.symbols" valueType="definedSymbols"&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="DEBUG_EFM=1"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="DEBUG=1"/&gt;</span><br/>
<span>-<span> </span>&lt;listOptionValue builtIn="false" value="EFM32PG1B200F256GM48=1"/&gt;</span><br/>
<span>+<span> </span>&lt;listOptionValue builtIn="false" value="EFM32JG1B200F256GM48=1"/&gt;</span><br/>
<span> <span> </span>&lt;/option&gt;</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.builtin.59744490" name="Always branch to builtin functions (-fno-builtin)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.builtin" value="true" valueType="boolean"/&gt;</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.prolog.2095193964" name="Generate debugger-friendly prologs (-mno-sched-prolog)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.prolog" value="true" valueType="boolean"/&gt;</span><br/>
<span>@@ -47,7 +47,7 @@</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/emlib/inc&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/kits/common/drivers&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/CMSIS/Include&amp;quot;"/&gt;</span><br/>
<span>-<span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/Device/SiliconLabs/EFM32PG1B/Include&amp;quot;"/&gt;</span><br/>
<span>+<span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/Device/SiliconLabs/EFM32JG1B/Include&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;/option&gt;</span><br/>
<span> <span> </span>&lt;inputType id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.input.1259106684" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.input"/&gt;</span><br/>
<span> <span> </span>&lt;/tool&gt;</span><br/>
<span>@@ -121,7 +121,7 @@</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.def.symbols.1906527140" name="Defined symbols (-D)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.def.symbols" valueType="definedSymbols"&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="DEBUG_EFM=1"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="NDEBUG=1"/&gt;</span><br/>
<span>-<span> </span>&lt;listOptionValue builtIn="false" value="EFM32PG1B200F256GM48=1"/&gt;</span><br/>
<span>+<span> </span>&lt;listOptionValue builtIn="false" value="EFM32JG1B200F256GM48=1"/&gt;</span><br/>
<span> <span> </span>&lt;/option&gt;</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.builtin.1881027154" name="Always branch to builtin functions (-fno-builtin)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.builtin" value="false" valueType="boolean"/&gt;</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.prolog.1759032162" name="Generate debugger-friendly prologs (-mno-sched-prolog)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.prolog"/&gt;</span><br/>
<span>@@ -133,7 +133,7 @@</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/emlib/inc&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/kits/common/drivers&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/CMSIS/Include&amp;quot;"/&gt;</span><br/>
<span>-<span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/Device/SiliconLabs/EFM32PG1B/Include&amp;quot;"/&gt;</span><br/>
<span>+<span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/Device/SiliconLabs/EFM32JG1B/Include&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;/option&gt;</span><br/>
<span> <span> </span>&lt;inputType id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.input.2098567682" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.input"/&gt;</span><br/>
<span> <span> </span>&lt;/tool&gt;</span><br/>
<span>@@ -206,7 +206,7 @@</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.def.symbols.1801462641" name="Defined symbols (-D)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.def.symbols" valueType="definedSymbols"&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="DEBUG_EFM=1"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="DEBUG=1"/&gt;</span><br/>
<span>-<span> </span>&lt;listOptionValue builtIn="false" value="EFM32PG1B200F256GM48=1"/&gt;</span><br/>
<span>+<span> </span>&lt;listOptionValue builtIn="false" value="EFM32JG1B200F256GM48=1"/&gt;</span><br/>
<span> <span> </span>&lt;/option&gt;</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.builtin.711105496" name="Always branch to builtin functions (-fno-builtin)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.builtin" value="true" valueType="boolean"/&gt;</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.prolog.1497848589" name="Generate debugger-friendly prologs (-mno-sched-prolog)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.prolog" value="true" valueType="boolean"/&gt;</span><br/>
<span>@@ -218,7 +218,7 @@</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/emlib/inc&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/kits/common/drivers&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/CMSIS/Include&amp;quot;"/&gt;</span><br/>
<span>-<span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/Device/SiliconLabs/EFM32PG1B/Include&amp;quot;"/&gt;</span><br/>
<span>+<span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/Device/SiliconLabs/EFM32JG1B/Include&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;/option&gt;</span><br/>
<span> <span> </span>&lt;inputType id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.input.462471232" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.input"/&gt;</span><br/>
<span> <span> </span>&lt;/tool&gt;</span><br/>
<span>@@ -292,7 +292,7 @@</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.def.symbols.227214347" name="Defined symbols (-D)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.def.symbols" valueType="definedSymbols"&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="DEBUG_EFM=1"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="NDEBUG=1"/&gt;</span><br/>
<span>-<span> </span>&lt;listOptionValue builtIn="false" value="EFM32PG1B200F256GM48=1"/&gt;</span><br/>
<span>+<span> </span>&lt;listOptionValue builtIn="false" value="EFM32JG1B200F256GM48=1"/&gt;</span><br/>
<span> <span> </span>&lt;/option&gt;</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.builtin.856642787" name="Always branch to builtin functions (-fno-builtin)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.builtin" value="false" valueType="boolean"/&gt;</span><br/>
<span> <span> </span>&lt;option id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.prolog.2116127698" name="Generate debugger-friendly prologs (-mno-sched-prolog)" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.debug.prolog"/&gt;</span><br/>
<span>@@ -304,7 +304,7 @@</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/emlib/inc&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/kits/common/drivers&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/CMSIS/Include&amp;quot;"/&gt;</span><br/>
<span>-<span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/Device/SiliconLabs/EFM32PG1B/Include&amp;quot;"/&gt;</span><br/>
<span>+<span> </span>&lt;listOptionValue builtIn="false" value="&amp;quot;${StudioSdkPath}/Device/SiliconLabs/EFM32JG1B/Include&amp;quot;"/&gt;</span><br/>
<span> <span> </span>&lt;/option&gt;</span><br/>
<span> <span> </span>&lt;inputType id="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.input.686138013" superClass="com.silabs.ide.si32.gcc.cdt.managedbuild.tool.gnu.c.compiler.input"/&gt;</span><br/>
<span> <span> </span>&lt;/tool&gt;</span><br/>
<div>
<br/></div>
<div></div>
</div>