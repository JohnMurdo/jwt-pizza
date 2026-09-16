# Learning notes

## JWT Pizza code study and debugging

As part of `Deliverable ⓵ Development deployment: JWT Pizza`, start up the application and debug through the code until you understand how it works. During the learning process fill out the following required pieces of information in order to demonstrate that you have successfully completed the deliverable.

| User activity                                       | Frontend component | Backend endpoints | Database SQL |
| --------------------------------------------------- | ------------------ | ----------------- | ------------ |
| View home page                                      |home.jsx|none|none|
| Register new user<br/>(t@jwt.com, pw: test)         |register.tsx|[POST] /api/auth|'INSERT INTO user (name, email, password) VALUES (?, ?, ?)'<br>'SELECT id, name FROM store WHERE franchiseId=?'<br>'INSERT INTO userRole (userId, role, objectId) VALUES (?, ?, ?)''INSERT INTO auth (token, userId) VALUES (?, ?) ON DUPLICATE KEY UPDATE token=token'|
| Login new user<br/>(t@jwt.com, pw: test)            |login.tsx|[PUT] /api/auth|'SELECT * FROM user WHERE email=?'<br>'SELECT * FROM userRole WHERE userId=?'<br>'INSERT INTO auth (token, userId) VALUES (?, ?) ON DUPLICATE KEY UPDATE token=token'<br>
| Order pizza                                         |NONE|NONE|'SELECT * FROM menu'<br>'SELECT id, name FROM franchise WHERE name LIKE ? LIMIT 201 OFFSET 0'<br>'SELECT id, name FROM store WHERE franchiseId=?'|
| Verify pizza                                        |delivery.tsx|[POST] {{pizzaFactoryUrl}}/api/order/verify|none|
| View profile page                                   |NONE|NONE|NONE|
| View franchise<br/>(as diner)                       |NONE|NONE|'SELECT userId FROM auth WHERE token=?'<br>"SELECT objectId FROM userRole WHERE role='franchisee' AND userId=?"|
| Logout                                              |NONE|NONE|'SELECT userId FROM auth WHERE token=?'<br>'DELETE FROM auth WHERE token=?'<br>|
| View About page                                     |payment.tsx|/api/user/me|'SELECT userId FROM auth WHERE token=?'<br>'SELECT id, franchiseId, storeId, date FROM dinerOrder WHERE dinerId=? LIMIT 0,10'<br>'SELECT id, menuId, description, price FROM orderItem WHERE orderId=?'|
| View History page                                   |history.tsx|none|none|
| Login as franchisee<br/>(f@jwt.com, pw: franchisee) |NONE|                   |              |
| View franchise<br/>(as franchisee)                  |NONE|                   |              |
| Create a store                                      |NONE|                   |              |
| Close a store                                       |NONE|                   |              |
| Login as admin<br/>(a@jwt.com, pw: admin)           |NONE|                   |              |
| View Admin page                                     |NONE|                   |              |
| Create a franchise for t@jwt.com                    |NONE|                   |              |
| Close the franchise for t@jwt.com                   |NONE|                   |              |
