# PYJXC 进销存管理系统

![Vue.js](https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D)
![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white)

一个基于 Vue.js + Django + MySQL 的完整进销存管理系统，支持采购管理、销售管理、库存管理和工作流审批。

## 功能特性

### ✅ 核心功能模块
- **商品管理** - 商品分类、品牌、规格、价格管理
- **采购管理** - 采购订单、入库管理、退货管理
- **销售管理** - 销售订单、出库管理、退货管理
- **库存管理** - 库存查询、调拨、盘点、预警
- **供应商管理** - 供应商信息、价格协议管理
- **客户管理** - 客户信息、信用额度管理
- **工作流审批** - 多级审批流程、批量审批功能

### 🔧 技术特色
- **前后端分离架构** - Vue.js SPA + Django REST API
- **RESTful API设计** - 标准化的API接口设计
- **响应式界面** - 支持桌面和移动端访问
- **权限控制** - 基于角色的访问控制(RBAC)
- **实时数据** - 实时库存更新和状态监控
- **批量操作** - 支持批量导入、导出、审批

## 项目结构

```
pyjxc-inventory-system/
├── backend/                 # Django后端项目
│   ├── pyjxc_backend/       # Django主应用
│   ├── api/                # REST API接口
│   ├── models/             # 数据模型
│   ├── serializers/        # 序列化器
│   ├── views/              # 视图函数
│   ├── urls.py             # URL路由
│   ├── settings.py         # 配置文件
│   └── requirements.txt    # Python依赖
├── frontend/               # Vue.js前端项目
│   ├── src/                # 源代码
│   │   ├── components/     # Vue组件
│   │   ├── views/          # 页面视图
│   │   ├── router/         # 路由配置
│   │   ├── store/          # Vuex状态管理
│   │   ├── api/            # API接口调用
│   │   └── utils/          # 工具函数
│   ├── public/             # 静态资源
│   ├── package.json        # Node.js依赖
│   └── vite.config.js      # Vite配置
├── database/               # 数据库相关
│   ├── migrations/         # 数据库迁移文件
│   ├── schema.sql          # 数据库建表脚本
│   └── sample_data/        # 示例数据
├── docs/                   # 项目文档
│   ├── api/                # API接口文档
│   ├── deployment/         # 部署文档
│   ├── user/               # 用户手册
│   └── development/        # 开发指南
├── scripts/                # 自动化脚本
│   ├── deployment/         # 部署脚本
│   ├── testing/           # 测试脚本
│   └── backup/            # 数据备份脚本
└── config/                 # 配置文件
    ├── nginx/             # Nginx配置
    ├── uwsgi/             # uWSGI配置
    └── environment/       # 环境变量配置
```

## 快速开始

### 环境要求
- Python 3.8+
- Node.js 16+
- MySQL 5.7+
- Git

### 1. 克隆项目

```bash
git clone https://github.com/jesterqq/pyjxc-inventory-system.git
cd pyjxc-inventory-system
```

### 2. 后端配置

```bash
cd backend
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate

pip install -r requirements.txt

# 配置环境变量
cp .env.example .env
# 编辑.env文件，配置数据库连接信息

# 数据库迁移
python manage.py migrate

# 创建超级用户
python manage.py createsuperuser

# 启动开发服务器
python manage.py runserver
```

### 3. 前端配置

```bash
cd frontend
npm install

# 配置环境变量
cp .env.example .env

# 启动开发服务器
npm run dev
```

### 4. 访问系统

- 前端地址: http://localhost:3000
- 后端API: http://localhost:8000
- 管理后台: http://localhost:8000/admin

## 功能演示

### 商品管理
- 商品分类管理，支持多级分类
- 商品信息管理，支持SKU、规格、价格
- 品牌管理，关联商品信息
- 商品图片上传和展示

### 采购管理
- 采购申请和审批流程
- 采购订单创建和管理
- 采购入库和验收
- 采购退货处理

### 销售管理
- 销售订单创建和管理
- 客户信用额度和价格策略
- 销售出库和发货管理
- 销售退货和售后处理

### 库存管理
- 实时库存查询和监控
- 库存调拨和转移
- 库存盘点和差异调整
- 库存预警和缺货提醒

### 工作流审批
- 可视化审批流程配置
- 多级审批和条件控制
- 批量审批功能
- 审批历史记录

## API文档

详细的API接口文档请参考 [API文档](./docs/api/README.md)

### 主要API端点

```
GET    /api/products/           # 商品列表
POST   /api/products/           # 创建商品
GET    /api/products/{id}/      # 商品详情
PUT    /api/products/{id}/      # 更新商品
DELETE /api/products/{id}/      # 删除商品

GET    /api/purchase-orders/    # 采购订单列表
POST   /api/purchase-orders/    # 创建采购订单
GET    /api/sales-orders/       # 销售订单列表
POST   /api/sales-orders/       # 创建销售订单

GET    /api/inventory/          # 库存查询
POST   /api/inventory/transfer/ # 库存调拨
POST   /api/inventory/check/    # 库存盘点

GET    /api/workflow/           # 工作流状态
POST   /api/workflow/approve/   # 审批操作
GET    /api/workflow/history/   # 审批历史
```

## 部署指南

### 开发环境部署

详细开发环境配置请参考 [开发环境配置文档](./docs/deployment/development.md)

### 生产环境部署

生产环境部署指南请参考 [生产环境部署文档](./docs/deployment/production.md)

## 贡献指南

我们欢迎任何形式的贡献！请查看 [贡献指南](./CONTRIBUTING.md) 了解如何参与项目开发。

### 开发流程

1. Fork 项目仓库
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 创建 Pull Request

## 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 联系方式

- 项目主页: https://github.com/jesterqq/pyjxc-inventory-system
- 问题反馈: [GitHub Issues](https://github.com/jesterqq/pyjxc-inventory-system/issues)
- 邮箱: [在此添加联系方式]

## 更新日志

### v1.0.0 (2025-11-11)
- ✅ 基础进销存功能实现
- ✅ 工作流审批系统
- ✅ 前后端分离架构
- ✅ 响应式界面设计
- ✅ 完整的API文档

---

**注意**: 本项目仍在积极开发中，欢迎提出建议和反馈！
