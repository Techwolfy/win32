---
title: To Get Writer Statistics
description: To Get Writer Statistics
ms.assetid: 81d7f567-0d99-4199-9248-1a497dc2eaab
keywords:
- Advanced Systems Format (ASF),writer statistics
- ASF (Advanced Systems Format),writer statistics
- writer statistics,about
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# To Get Writer Statistics

The writer can provide statistical information about writing operations. There are two methods for gathering writer statistics: [**IWMWriterAdvanced::GetStatistics**](/windows/desktop/api/Wmsdkidl/nf-wmsdkidl-iwmwriteradvanced-getstatistics) and [**IWMWriterAdvanced3::GetStatisticsEx**](/windows/desktop/api/Wmsdkidl/nf-wmsdkidl-iwmwriteradvanced3-getstatisticsex). The information retrieved by **GetStatisticsEx** is more specific than the information retrieved by **GetStatistics**.

Both methods populate structures with statistical information. **GetStatistics** uses the [**WM\_WRITER\_STATISTICS**](/windows/desktop/api/Wmsdkidl/ns-wmsdkidl-_wmwriterstatistics) structure, and **GetStatisticsEx** uses the [**WM\_WRITER\_STATISTICS\_EX**](/windows/desktop/api/Wmsdkidl/ns-wmsdkidl-_wmwriterstatisticsex) structure. **GetStatisticsEx** does not duplicate the data obtained by **GetStatistics**. For the most complete information, you should call both methods.

## Related topics

<dl> <dt>

[**IWMWriterAdvanced Interface**](/windows/desktop/api/wmsdkidl/nn-wmsdkidl-iwmwriteradvanced)
</dt> <dt>

[**IWMWriterAdvanced3 Interface**](/windows/desktop/api/wmsdkidl/nn-wmsdkidl-iwmwriteradvanced3)
</dt> <dt>

[**Writing ASF Files**](writing-asf-files.md)
</dt> </dl>

 

 



