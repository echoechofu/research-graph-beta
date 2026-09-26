# 期刊数据配置与致谢 / Journal data setup and acknowledgment

## 中文

感谢第三方项目 [hitfyd/ShowJCR](https://github.com/hitfyd/ShowJCR) 对期刊数据的整理与来源参考。应用当前适配其 `JCR2025-UTF8.csv` 结构。本仓库提供配置说明，不镜像其数据文件，也不保证与上游最新数据同步。

### 导入步骤

1. 从你有权使用的来源取得 CSV，例如所在机构授权的 JCR 数据导出。第三方来源可作为格式参考，使用权需另行确认。
2. 使用 UTF-8 CSV，大小不超过 20 MB；至少包含可识别的期刊名称和分区字段。当前适配格式使用 `Journal`、`IF Quartile(2025)_1` 等列，`ISSN` 和 `EISSN` 可提高匹配准确率。
3. 打开个人知识库的“设置”，点击“导入期刊 CSV”，选择文件。
4. 导入成功后检查期刊门控状态和已加载期刊数量，再预览文献。

导入不会自动改写已有 Claim 或学习笔记。期刊分区仅用于文献准入筛选，不是单篇论文或研究结论的证据分级。

### 使用与权利说明

本项目面向个人学习与研究，不提供第三方数据的商业用途授权。Journal Citation Reports（JCR）是 Clarivate 产品。ShowJCR 的软件许可证不自动赋予我们对第三方数据的再许可权；来源署名和个人使用声明不替代适用许可。本项目不隶属于或获得 Clarivate 认可。参见 [JCR 官方引用与许可说明](https://journalcitationreports.zendesk.com/hc/en-gb/articles/28351332957201-Citing-the-Journal-Citation-Reports)。

## English

Thanks to [hitfyd/ShowJCR](https://github.com/hitfyd/ShowJCR) for preparing the third-party journal data and providing a source reference. The app supports its `JCR2025-UTF8.csv` structure. This repository provides setup instructions, not a dataset mirror or a guarantee of upstream synchronization.

### Import steps

1. Obtain a CSV from a source you are entitled to use, such as your institution's authorized JCR export. Third-party sources may serve as format references; verify rights separately.
2. Use UTF-8 CSV, at most 20 MB, with recognized journal-name and quartile fields. The supported layout uses columns such as `Journal` and `IF Quartile(2025)_1`; `ISSN` and `EISSN` improve matching.
3. Open Settings in Personal Research Graph, choose “Import journal CSV,” and select the file.
4. Check the journal gate status and loaded journal count before previewing papers.

Importing does not automatically rewrite existing claims or learning notes. Quartiles are an intake filter, not an evidence grade for individual papers or findings.

### Use and rights

This project is intended for personal learning and research and grants no commercial-use rights to third-party data. Journal Citation Reports is a Clarivate product. ShowJCR's software license does not automatically grant us the right to relicense third-party data. Attribution and personal-use notices do not replace applicable terms. This project is not affiliated with or endorsed by Clarivate. See [official citation and permissions guidance](https://journalcitationreports.zendesk.com/hc/en-gb/articles/28351332957201-Citing-the-Journal-Citation-Reports).
