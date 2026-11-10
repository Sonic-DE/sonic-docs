---
title: System Monitor
description: See what your computer is doing, and stop or slow down programs that misbehave.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-system-monitor da5f6699 (src/Main.qml, src/GlobalMenu.qml, src/ToolsModel.cpp, src/pages/, src/page/PageDialog.qml, src/page/PageSortDialog.qml, src/page/EditablePage.qml, src/page/RowControl.qml, src/page/ColumnControl.qml, src/page/FaceConfigurationPage.qml, src/faces/processtable, src/faces/applicationstable, src/table/ReniceDialog.qml, src/table/ColumnConfigurationDialog.qml, org.kde.plasma-systemmonitor.desktop); written from the code, not clicked through"
---

# System Monitor

System Monitor shows how busy your computer is and which programs are running. You can end a program that has stopped responding, change how much processor time it gets, and build your own pages of charts.

Open it from the application launcher, with Meta+Esc, or by running `plasma-systemmonitor`. Right-clicking it in the launcher offers **Open Overview Page**, **Open History Page**, **Open Processes Page** and **Open Applications Page**.

## Pages

The sidebar lists the pages. System Monitor comes with four:

- **Overview:** the current network, processor, graphics processor, memory and disk use.
- **Applications:** the applications you're running, with what each one uses.
- **History:** charts of processor, memory and network use over time.
- **Processes:** every process on the system.

At the top of the sidebar, **Tools** starts related programs when they're installed, such as System Log, Info Center and `htop`, and has **Kill a Window…**, which lets you click a window to force it to close. **Collapse Sidebar** and **Expand Sidebar** make the sidebar narrow or wide again; you can also drag its edge.

## Applications

The Applications page groups each application with its helper processes, so the totals include everything the application runs. A terminal's totals include its shells and the jobs in them. Processes that don't clearly belong to an application are listed under **Background Services**.

- **Search** filters the list.
- **Quit Application** asks the selected application to close, after a confirmation that warns about unsaved work unless you've turned it off.
- **Show Details Sidebar** shows the CPU, memory, network and disk use of the selected application.
- **Configure Columns…** chooses the columns.

Right-click an application for **Set priority…**, **Send Signal** and **Quit Application**. Sending **Kill (KILL)** forces it to quit. Right-click a column header to **Hide** that column.

## Processes

- **Search** filters the list.
- **End Process** (Delete) ends the selected processes, after a confirmation that warns about unsaved work unless you've turned it off. Shift+Delete ends them forcibly (SIGKILL), and F8 opens **Set priority…**. The same keys work on the Applications page.
- **Display as List** or **Display as Tree**, where each process is shown under the one that started it.
- **Show:** **Own Processes**, **User Processes**, **System Processes** or **All Processes**.
- **Configure Columns…** chooses the columns.

Right-click a process for:

- **Set priority…**, described below.
- **Send Signal**: **Suspend (STOP)**, **Continue (CONT)**, **Hangup (HUP)**, **Interrupt (INT)**, **Terminate (TERM)**, **Kill (KILL)**, **User 1 (USR1)** or **User 2 (USR2)**.
- **Copy Current Column** copies the value under the pointer.
- **End Process**.

Right-click a column header to **Hide** that column.

### Setting a priority

**Set Priority** changes how the system shares time between processes. Under **CPU Scheduler**, choose **Normal**, **Batch** (for CPU-intensive work that isn't interactive), **Round robin** or **FIFO** (both run the process whenever it can run, with and without time slices), and move the slider between **Low priority** and **High priority**. Under **I/O Scheduler**, choose **Normal** (based on the CPU priority), **Idle** (only uses the disk when nothing else does), **Best Effort** or **Real Time**, with its own priority slider.

### Columns

**Configure Columns…** lists the enabled columns and the others. Drag a column by its handle to change the order, and choose how each one is shown: **Hidden**, **Text Only**, **Line Chart**, or for some columns **Text Only (Scaled to 100%)** and **Line Chart (Scaled to 100%)**.

## Making your own pages

- **Add New Page…** creates a page. Give it a **Name:** and an **Icon:**, choose **Page Margins:** (**None**, **Small** or **Large**), which page's toolbar actions it shows with **Use Actions From:**, and whether **Load this page:** **When needed** or **During application startup**.
- **Edit Page**, at the top of a page, lets you change it: **Add Row**, **Add Title**, and in a row **Add Column**, with a **Height** of **Balanced**, **Minimum**, **Maximum** or **Half Page Height**. A column can **Add Section**, **Add Separator**, **Show Background** and **Remove Background Margins**. **Configure Page…** changes the name, icon and other settings. **Save Changes** or **Discard Changes** ends editing.
- Each chart has its own settings: a **Title**, a **Display Style**, the sensors to show and **Minimum time between updates:**. **Save Settings as Preset** and **Load Preset…** reuse settings, and **Add Chart as Desktop Widget** puts the same chart on your desktop.
- **Edit or Remove pages…** reorders the pages and has **Show Page**, **Hide Page**, **Reset** (back to how it was installed) and **Remove**. **Start with:** chooses which page opens when System Monitor starts, or **Last Visited Page**.
- **Export Current Page…** saves a page as a `.page` file, **Import Page…** loads one, and **Get New Pages…** downloads pages made by others.

These are in the sidebar's menu, and in the File, View and Settings menus of the global menu if you use one.

For the Processes and Applications tables, the chart settings also have **Show toolbar**, **Confirm ending processes** (or **Confirm when quitting applications**), **By default show:** for the Processes table, and **Show details panel** for the Applications table.
