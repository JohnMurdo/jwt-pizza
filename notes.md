# Learning notes

## JWT Pizza code study and debugging

As part of `Deliverable ⓵ Development deployment: JWT Pizza`, start up the application and debug through the code until you understand how it works. During the learning process fill out the following required pieces of information in order to demonstrate that you have successfully completed the deliverable.

| User activity                                       | Frontend component | Backend endpoints | Database SQL |
| --------------------------------------------------- | ------------------ | ----------------- | ------------ |
| View home page                                      |home.jsx|none|none|
| Register new user<br/>(t@jwt.com, pw: test)         |register.tsx|[POST] /api/auth|'INSERT INTO user (name, email, password) VALUES (?, ?, ?)'<br>'SELECT id, name FROM store WHERE franchiseId=?'<br>'INSERT INTO userRole (userId, role, objectId) VALUES (?, ?, ?)''INSERT INTO auth (token, userId) VALUES (?, ?) ON DUPLICATE KEY UPDATE token=token'|
| Login new user<br/>(t@jwt.com, pw: test)            |login.tsx|[PUT] /api/auth|'SELECT * FROM user WHERE email=?'<br>'SELECT * FROM userRole WHERE userId=?'<br>'INSERT INTO auth (token, userId) VALUES (?, ?) ON DUPLICATE KEY UPDATE token=token'<br>
| Order pizza                                         |                    |[POST] /api/order|'SELECT * FROM menu'<br>'INSERT INTO dinerOrder (dinerId, franchiseId, storeId, date) VALUES (?, ?, ?, now())'<br>'SELECT id FROM menu WHERE id=?'<br>'INSERT INTO orderItem (orderId, menuId, description, price) VALUES (?, ?, ?, ?)'|
| Verify pizza                                        |delivery.tsx|[POST] {{pizzaFactoryUrl}}/api/order/verify|none|
| View profile page                                   |dinerDashboard.tsx|none|'SELECT userId FROM auth WHERE token=?'<br>'SELECT id, franchiseId, storeId, date FROM dinerOrder WHERE dinerId=? LIMIT 0,10'|
| View franchise<br/>(as diner)                       |                    |                   |'SELECT userId FROM auth WHERE token=?'<br>"SELECT objectId FROM userRole WHERE role='franchisee' AND userId=?"|
| Logout                                              |                    |                   |'SELECT userId FROM auth WHERE token=?'<br>'DELETE FROM auth WHERE token=?'<br>|
| View About page                                     |payment.tsx|/api/user/me|'SELECT userId FROM auth WHERE token=?'<br>'SELECT id, franchiseId, storeId, date FROM dinerOrder WHERE dinerId=? LIMIT 0,10'<br>'SELECT id, menuId, description, price FROM orderItem WHERE orderId=?'|
| View History page                                   |history.tsx|none|none|
| Login as franchisee<br/>(f@jwt.com, pw: franchisee) |                    |                   |'SELECT * FROM user WHERE email=?'<br>'SELECT * FROM userRole WHERE userId=?'<br>'INSERT INTO auth (token, userId) VALUES (?, ?) ON DUPLICATE KEY UPDATE token=token'|
| View franchise<br/>(as franchisee)                  |                    |                   |              |
| Create a store                                      |                    |                   |              |
| Close a store                                       |                    |                   |              |
| Login as admin<br/>(a@jwt.com, pw: admin)           |                    |                   |              |
| View Admin page                                     |                    |                   |              |
| Create a franchise for t@jwt.com                    |                    |                   |              |
| Close the franchise for t@jwt.com                   |                    |                   |              |
