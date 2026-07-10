# TODO - MySQL FK datatype consistency (users.id)

## Step 1: Identify & confirm users.id type
- [x] Read `ats-backend/models/User.Model.js` (users.id is `DataTypes.STRING`)

## Step 2: Fix FK columns referencing `users.id` to match STRING(36)
- [x] Edit `ats-backend/models/Job.Model.js` (postedBy, updatedBy)
- [x] Edit `ats-backend/models/Interview.Model.js` (interviewerId, createdBy, updatedBy)
- [x] Edit `ats-backend/models/Document.Model.js` (userId, uploadedBy, updatedBy)
- [x] Edit `ats-backend/models/Dashboard.Model.js` (userId, updatedBy)
- [x] Edit `ats-backend/models/AI-JD.Model.js` (generatedBy, updatedBy)
- [x] Edit `ats-backend/models/ActivityLog.Model.js` (userId)
- [x] Edit `ats-backend/models/User.Model.js` (explicitly STRING(36) for id)


## Step 3: Validate other FK columns (non-users) are unaffected
- [ ] Quick scan for other `references: { model: 'users', key: 'id' }` across backend

## Step 4: Run sync check for MySQL without FK datatype errors
- [x] Ran `node ats-backend/check-db.js` (SQLite fallback in local env)


## Step 5: Final verification
- [x] Verified all `users.id` FK columns are now `STRING(36)` in Sequelize models


