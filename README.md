# db-42233060
2025-春 数据库原理作业
# week2 Relational Model
数据模型是描述数据、数据联系、数据语义以及一致性约束的概念工具的集合。本周我们学习的是**关系模型**。此外，为了理解关系数据库查询语言的理论基础，我们还学习了**关系代数**。

# （第1次作业）
## 题目一（3分+4分）
考虑一个`银行`数据库，其关系模式如下所示：

- branch (branch_name, branch_city, assets)
- customer (ID, customer_name, customer_street, customer_city)
- loan (loan_number, branch_name, amount)
- borrower (ID, loan_number)
- account (account_number, branch_name, balance)
- depositor (ID, account_number)

使用`关系代数`完成下面的查询：

1. 找到位于`成都`市的支行的名字。

$\pi_{branch_{-}name}(\sigma_{branch_{-}city='成都'}(branch))$


2. 找到在`杨柳`支行有贷款（`loan`）的借款人（`borrower`）的ID。

$\pi_{ID}(\sigma_{branch_{-}name='杨柳'}(loan\bowtie borrower))$

## 题目二（3分）
假设数据库中存储用户名和密码的关系模式是 users(name, pswd, gender)，请结合关系代数简述实现`用户登录`逻辑的思路。

用户登录过程中，系统验证输入的用户名、密码和性别是否与数据库中储存的记录相匹配，假设用户输入的用户名为**name1**，密码为**pswd1**，性别为**gender1**。
如果

$\sigma_{name = name1\land pswd = pswd1\land gender=gender1}(users)$

若表达式返回的关系非空，则说明数据库中存在与用户输入匹配的记录，则登录成功；反之则登录失败。

