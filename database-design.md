# 女性历史爱好者个人成长知识库 - 数据库设计

## 1. 数据库架构概述

本项目采用关系型数据库设计，主要包含以下核心模块：
- 女性成长库
- 历史典籍库
- 文物鉴赏库
- 影视清单库
- 记录访谈库
- 顶尖大师课
- 实用工具库
- 用户管理

## 2. 数据模型设计

### 2.1 用户表 (users)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 用户ID |
| username | VARCHAR(50) | UNIQUE, NOT NULL | 用户名 |
| email | VARCHAR(100) | UNIQUE, NOT NULL | 邮箱 |
| password_hash | VARCHAR(255) | NOT NULL | 密码哈希 |
| avatar | VARCHAR(255) | | 头像URL |
| bio | TEXT | | 个人简介 |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |
| updated_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | 更新时间 |

### 2.2 女性成长库 (growth_resources)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 资源ID |
| title | VARCHAR(100) | NOT NULL | 标题 |
| type | ENUM('book', 'article', 'course', 'tool') | NOT NULL | 资源类型 |
| author | VARCHAR(100) | | 作者/创建者 |
| description | TEXT | NOT NULL | 描述 |
| content | TEXT | | 详细内容 |
| cover_image | VARCHAR(255) | | 封面图片URL |
| external_link | VARCHAR(255) | | 外部链接 |
| publish_date | DATE | | 发布日期 |
| category | VARCHAR(50) | | 分类 |
| tags | VARCHAR(255) | | 标签 |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |
| updated_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | 更新时间 |

### 2.3 历史典籍库 (historical_books)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 典籍ID |
| title | VARCHAR(100) | NOT NULL | 书名 |
| author | VARCHAR(100) | | 作者 |
| dynasty | VARCHAR(50) | | 朝代/时期 |
| description | TEXT | NOT NULL | 描述 |
| content | TEXT | | 原文内容 |
| translation | TEXT | | 译文 |
| cover_image | VARCHAR(255) | | 封面图片URL |
| publication_year | INT | | 出版年份 |
| category | VARCHAR(50) | | 分类 |
| tags | VARCHAR(255) | | 标签 |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |
| updated_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | 更新时间 |

### 2.4 文物鉴赏库 (cultural_artifacts)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 文物ID |
| name | VARCHAR(100) | NOT NULL | 文物名称 |
| era | VARCHAR(50) | NOT NULL | 时代 |
| type | VARCHAR(50) | NOT NULL | 类型 |
| description | TEXT | NOT NULL | 描述 |
| material | VARCHAR(100) | | 材质 |
| origin | VARCHAR(100) | | 出土地/产地 |
| collection | VARCHAR(100) | | 收藏机构 |
| images | TEXT | | 图片URL（JSON数组） |
| video_link | VARCHAR(255) | | 视频链接 |
| category | VARCHAR(50) | | 分类 |
| tags | VARCHAR(255) | | 标签 |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |
| updated_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | 更新时间 |

### 2.5 影视清单库 (media_resources)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 影视ID |
| title | VARCHAR(100) | NOT NULL | 标题 |
| type | ENUM('movie', 'tv_series', 'documentary', 'video') | NOT NULL | 类型 |
| director | VARCHAR(100) | | 导演 |
| actors | TEXT | | 演员阵容 |
| description | TEXT | NOT NULL | 描述 |
| release_year | INT | | 发行年份 |
| duration | VARCHAR(50) | | 时长 |
| cover_image | VARCHAR(255) | | 封面图片URL |
| trailer_link | VARCHAR(255) | | 预告片链接 |
| watch_link | VARCHAR(255) | | 观看链接 |
| rating | DECIMAL(3,1) | | 评分 |
| category | VARCHAR(50) | | 分类 |
| tags | VARCHAR(255) | | 标签 |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |
| updated_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | 更新时间 |

### 2.6 记录访谈库 (interviews)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 访谈ID |
| title | VARCHAR(100) | NOT NULL | 标题 |
| interviewee | VARCHAR(100) | NOT NULL | 被访谈者 |
| interviewer | VARCHAR(100) | | 访谈者 |
| description | TEXT | NOT NULL | 描述 |
| content | TEXT | | 访谈内容 |
| interview_date | DATE | | 访谈日期 |
| publish_date | DATE | | 发布日期 |
| cover_image | VARCHAR(255) | | 封面图片URL |
| audio_link | VARCHAR(255) | | 音频链接 |
| video_link | VARCHAR(255) | | 视频链接 |
| category | VARCHAR(50) | | 分类 |
| tags | VARCHAR(255) | | 标签 |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |
| updated_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | 更新时间 |

### 2.7 顶尖大师课 (masterclasses)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 课程ID |
| title | VARCHAR(100) | NOT NULL | 课程标题 |
| instructor | VARCHAR(100) | NOT NULL | 讲师 |
| description | TEXT | NOT NULL | 描述 |
| syllabus | TEXT | | 课程大纲 |
| duration | VARCHAR(50) | | 课程时长 |
| cover_image | VARCHAR(255) | | 封面图片URL |
| video_link | VARCHAR(255) | | 视频链接 |
| start_date | DATE | | 开始日期 |
| end_date | DATE | | 结束日期 |
| price | DECIMAL(10,2) | | 价格 |
| rating | DECIMAL(3,1) | | 评分 |
| category | VARCHAR(50) | | 分类 |
| tags | VARCHAR(255) | | 标签 |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |
| updated_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | 更新时间 |

### 2.8 实用工具库 (tools)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 工具ID |
| name | VARCHAR(100) | NOT NULL | 工具名称 |
| type | VARCHAR(50) | NOT NULL | 工具类型 |
| description | TEXT | NOT NULL | 描述 |
| usage_guide | TEXT | | 使用指南 |
| tool_link | VARCHAR(255) | | 工具链接 |
| cover_image | VARCHAR(255) | | 封面图片URL |
| category | VARCHAR(50) | | 分类 |
| tags | VARCHAR(255) | | 标签 |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |
| updated_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | 更新时间 |

### 2.9 评论表 (comments)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 评论ID |
| user_id | INT | FOREIGN KEY REFERENCES users(id) | 用户ID |
| resource_type | ENUM('growth', 'history', 'cultural', 'media', 'interview', 'masterclass', 'tool') | NOT NULL | 资源类型 |
| resource_id | INT | NOT NULL | 资源ID |
| content | TEXT | NOT NULL | 评论内容 |
| rating | INT | CHECK (rating BETWEEN 1 AND 5) | 评分 |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |
| updated_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP | 更新时间 |

### 2.10 收藏表 (collections)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 收藏ID |
| user_id | INT | FOREIGN KEY REFERENCES users(id) | 用户ID |
| resource_type | ENUM('growth', 'history', 'cultural', 'media', 'interview', 'masterclass', 'tool') | NOT NULL | 资源类型 |
| resource_id | INT | NOT NULL | 资源ID |
| created_at | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 创建时间 |

### 2.11 浏览历史表 (browse_history)
| 字段名 | 数据类型 | 约束 | 描述 |
|-------|---------|------|------|
| id | INT | PRIMARY KEY, AUTO_INCREMENT | 历史ID |
| user_id | INT | FOREIGN KEY REFERENCES users(id) | 用户ID |
| resource_type | ENUM('growth', 'history', 'cultural', 'media', 'interview', 'masterclass', 'tool') | NOT NULL | 资源类型 |
| resource_id | INT | NOT NULL | 资源ID |
| view_time | TIMESTAMP | DEFAULT CURRENT_TIMESTAMP | 浏览时间 |

## 3. 数据关系图

```
+----------+       +---------------+
|  users   |<------+  collections  |
+----------+       +---------------+
|          |       |               |
|          |       +---------------+
|          |       |  browse_history |
|          |<------+---------------+
|          |       |               |
|          |       +---------------+
|          |       |   comments    |
+----------+<------+---------------+

+---------------+    +-----------------+    +------------------+
| growth_resources | | historical_books | | cultural_artifacts |
+---------------+    +-----------------+    +------------------+

+------------------+    +------------------+    +------------------+
| media_resources  |    |    interviews    |    |  masterclasses   |
+------------------+    +------------------+    +------------------+

+------------------+
|      tools       |
+------------------+
```

## 4. 索引设计

为提高查询性能，建议在以下字段上创建索引：

- 用户表：email, username
- 各资源表：title, category, tags
- 评论表：resource_type, resource_id
- 收藏表：user_id, resource_type
- 浏览历史表：user_id, view_time

## 5. 数据迁移与初始化

### 5.1 初始化数据
- 女性成长库：导入经典成长书籍、文章和工具
- 历史典籍库：导入重要历史文献和研究资料
- 文物鉴赏库：导入精选文物资料和图片
- 影视清单库：导入推荐影视作品和纪录片
- 记录访谈库：导入重要访谈记录
- 顶尖大师课：导入优质课程信息
- 实用工具库：导入实用工具和资源

### 5.2 数据迁移策略
- 使用数据库迁移工具（如Flyway或Liquibase）管理 schema 变更
- 定期备份数据，确保数据安全
- 建立数据同步机制，保持数据一致性

## 6. 扩展性考虑

- **分库分表**：当数据量增长时，可考虑按模块分库或按时间分表
- **缓存策略**：对热门资源使用缓存，提高访问速度
- **全文搜索**：集成全文搜索功能，提升用户搜索体验
- **数据分析**：建立数据仓库，分析用户行为和资源使用情况

## 7. 安全性考虑

- **数据加密**：对用户密码和敏感信息进行加密存储
- **访问控制**：实现基于角色的访问控制
- **SQL注入防护**：使用参数化查询，防止SQL注入攻击
- **XSS防护**：对用户输入进行过滤和转义
- **CSRF防护**：实现CSRF令牌验证机制

## 8. 总结

本数据库设计方案为女性历史爱好者个人成长知识库提供了完整的数据结构和关系模型，支持各模块的功能需求，并为后续的扩展和优化预留了空间。设计注重数据的完整性、一致性和查询性能，同时考虑了安全性和可扩展性。