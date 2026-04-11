# pages 技术总结

## 职责定位

`frontend/src/pages/` 是路由页面集合，覆盖采集、翻译、导入导出、系统管理、个人中心等所有业务入口。

## 页面分组

| 业务域 | 页面示例 |
| --- | --- |
| 数据采集 | `DataStatisticsDashboard.vue`, `CollectionTaskManagement.vue`, `DataCollectionList.vue` |
| 时间段管理 | `TimePeriodManagement.vue`, `TimePeriodDetail.vue` |
| 翻译管理 | `TranslationConfigManagement.vue`, `TranslationTaskManagement.vue`, `TranslationResults.vue` |
| 导入导出 | `DataExport.vue`, `DataImport.vue`, `ImportExportHistory.vue` |
| 系统管理 | `AdminUsers.vue`, `AdminTeams.vue`, `DepartmentManagement.vue`, `AdminRoles.vue` |
| 个人与设置 | `Profile.vue`, `ProfileSetup.vue`, `Settings.vue`, `SetPassword.vue` |
| 登录注册 | `Login.vue`, `Register.vue`, `Home.vue` |

## 技术要点

- 页面命名与业务名高度一致，可读性好。
- 页面层数量较多，说明项目以功能完整度优先，而非极简前端架构。
- 采集、翻译、导入导出三条业务链路都已具备完整的前端承载页面。
