THEKKAN PORE SILAMBA KALAI — Firebase Attendance App (diagnostic build)

Files
- index.html: login, student list/profile, belt sorting, attendance, history and CSV exports.
- firestore.rules: secure Firestore rules template.

IMPORTANT: This ZIP improves the error message so it identifies which database step failed. No ZIP can guarantee that Firebase will work until the rules and Firebase Console setup are correct and the app is tested against your project.

Firebase project configured in this app: thekkanporeattendance-36c06

Required setup
1. Firebase Console > Authentication > Sign-in method: enable Email/Password.
2. Authentication > Users: create each master account manually. There is no public sign-up.
3. Copy that account's UID. In Firestore Database, create collection `masters`, then a document whose document ID is EXACTLY that UID. Add field `active` with type Boolean and value true (not a text/string value).
4. Publish the contents of firestore.rules in Firebase Console > Firestore Database > Rules.
5. Ensure you are working in project `thekkanporeattendance-36c06` and that the database is the default Firestore database.
6. For dependable use on phones, host index.html on an HTTPS static host. Opening a local file (file://) is not the recommended deployment method. This ZIP itself is not an installed/hosted app.
7. First test with fake student data. Do not enter Aadhaar or other unnecessary sensitive information.

If login still fails
The app will now show the exact stage and Firebase error code:
- `checking master approval document`: check the UID/document ID, active Boolean, rules publication and project.
- `loading students (collection: students)`: the master check passed, but the students query failed.
- `loading attendance ...`: the master check and student query passed, but attendance query failed.
Share only the displayed stage and error code/message. Never share your password or private service-account keys.

Collections
- masters/{Authentication UID}: { active: true } (admin-managed only)
- students: name, belt, dob, parentName, parentPhone, address
- attendance: studentId, date (YYYY-MM-DD), status, markedBy

The app is a starter version. Test thoroughly before storing real student records.
