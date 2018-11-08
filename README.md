Project for Reproduction of RDLC Designer Hang/Crash
====================================================

This project facilitates reproduction of a hang-then-crash bug in [Microsoft
RDLC Report Designer for Visual
Studio](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftRdlcReportDesignerforVisualStudio-18001)
14.2.  To reproduce:

1. Open `RdlcDesignerAddDatasetCrash.sln` in Microsoft Visual Studio Community
   2017 Version 15.8.9.
2. Run [`Update-Package
   -reinstall`](https://docs.microsoft.com/en-us/nuget/consume-packages/reinstalling-and-updating-packages)
   in the Package Manger Console.  **Important:** Restore is insufficient.
   Must reinstall to repopulate `bin` directory.
3. Open `Report.rdlc`.
4. Right-click on `Datasets` in the `Report Data` window, then click `Add
   Dataset...`.

At this point Visual Studio will freeze for about 50 seconds then restart.

I suspect that this is due to the presence of an `.xsd` file which is not a
[Typed
Dataset](https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/dataset-datatable-dataview/typed-datasets)
in the `App_Data` directory.
