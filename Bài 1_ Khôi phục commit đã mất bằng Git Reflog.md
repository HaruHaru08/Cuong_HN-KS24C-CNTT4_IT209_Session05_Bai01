Bài 1: Khôi phục commit đã mất bằng Git Reflog

\#\# 1\. Chuẩn bị  
Tạo repo thử nghiệm, commit nền \`Initial commit\`, sau đó tạo \`feature.txt\`  
(nội dung: \`Day la tinh nang quan trong\`) và commit \`Them tinh nang quan trong\`.

\#\# 2\. Phát hiện mất commit  
Chạy \`git reset \--hard HEAD\~1\` để giả lập sự cố. Kiểm tra bằng \`git log \--oneline\`  
thì commit \`Them tinh nang quan trong\` đã biến mất, \`feature.txt\` cũng không còn.

\#\# 3\. Tra cứu reflog  
Chạy \`git reflog\`, tìm được dòng \`e3a5b2c HEAD@{1}: commit: Them tinh nang quan trong\`.  
Mã hash \`e3a5b2c\` là commit đã mất.

\#\# 4\. Khôi phục  
Chạy \`git reset \--hard e3a5b2c\`. Git đưa nhánh \`main\` về lại commit cũ.

\#\# 5\. Kiểm tra kết quả  
\`git log \--oneline\` hiển thị lại commit \`Them tinh nang quan trong\`,  
file \`feature.txt\` xuất hiện lại đúng nội dung ban đầu.

\#\# 6\. Giải thích cơ chế  
Reflog ghi lại mọi lần HEAD di chuyển ở máy cục bộ. Sau \`reset \--hard\`, commit không bị  
xóa ngay mà chỉ không còn được nhánh nào trỏ tới, nên vẫn tìm được hash qua reflog  
và đưa nhánh trỏ lại.

