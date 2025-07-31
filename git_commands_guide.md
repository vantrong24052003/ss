# Hướng dẫn Git Commands cho Intern 🚀

> Tài liệu này bao gồm các lệnh Git cơ bản mà mọi intern cần nắm vững

---

## 📌 Git Branch

### Xem danh sách branch
```bash
git branch         # Branch local
git branch -r      # Branch remote  
git branch -a      # Tất cả branch
```

### Tạo và chuyển branch
```bash
# Tạo branch mới
git branch <tên-branch>

# Tạo và chuyển sang branch mới (khuyến nghị)
git checkout -b <tên-branch>

# Cách mới (Git 2.23+)
git switch -c <tên-branch>
```

### Chuyển branch
```bash
git checkout <tên-branch>
git switch <tên-branch>       # Cách mới
```

### Xóa branch
```bash
git branch -d <tên-branch>    # Xóa an toàn
git branch -D <tên-branch>    # Xóa bắt buộc (cẩn thận!)
```

---

## 📥 Git Pull

### Pull cơ bản
```bash
git pull                      # Pull từ branch hiện tại
git pull origin main          # Pull từ branch main
git pull origin <tên-branch>  # Pull từ branch cụ thể
```

### Pull với rebase (khuyến nghị)
```bash
git pull --rebase
git pull --rebase origin main
```

> **💡 Tip**: Sử dụng `--rebase` để có history commit sạch hơn

---

## 🔀 Git Merge

### Merge cơ bản
```bash
# Merge branch khác vào branch hiện tại
git merge <tên-branch>

# Merge với message tùy chỉnh
git merge <tên-branch> -m "Merge message"
```

### Các tùy chọn merge
```bash
# Fast-forward merge (không tạo commit merge)
git merge --ff-only <tên-branch>

# Luôn tạo commit merge
git merge --no-ff <tên-branch>

# Hủy merge khi có conflict
git merge --abort
```

---

## ↩️ Git Reset

### Các loại reset
```bash
# Reset soft - giữ changes trong staging area
git reset --soft HEAD~1

# Reset mixed (mặc định) - giữ changes trong working directory
git reset HEAD~1
git reset --mixed HEAD~1

# Reset hard - XÓA TẤT CẢ CHANGES (NGUY HIỂM!)
git reset --hard HEAD~1
git reset --hard <commit-hash>
```

### Reset file cụ thể
```bash
git reset HEAD <tên-file>     # Unstage file
```

> **⚠️ Cảnh báo**: `--hard` sẽ xóa tất cả thay đổi, hãy cẩn thận!

---

## 🔄 Git Rebase

### Rebase cơ bản
```bash
# Rebase branch hiện tại lên branch khác
git rebase main
git rebase origin/main
```

### Interactive rebase
```bash
# Edit 3 commits gần nhất
git rebase -i HEAD~3

# Edit từ commit cụ thể
git rebase -i <commit-hash>
```

### Xử lý rebase
```bash
# Tiếp tục sau khi resolve conflicts
git rebase --continue

# Hủy rebase
git rebase --abort

# Skip commit hiện tại
git rebase --skip
```

---

## 🚀 Workflow Cơ Bản cho Intern

### 1. Bắt đầu làm feature mới
```bash
# Cập nhật code mới nhất
git checkout main
git pull origin main

# Tạo branch mới
git checkout -b feature/ten-feature
```

### 2. Làm việc và commit
```bash
git add .
git commit -m "Add new feature"
```

### 3. Push lên remote
```bash
git push origin feature/ten-feature
```

### 4. Merge vào main (sau khi PR approved)
```bash
git checkout main
git pull origin main
git merge feature/ten-feature
git push origin main
```

### 5. Dọn dẹp
```bash
# Xóa branch local
git branch -d feature/ten-feature

# Xóa branch remote
git push origin --delete feature/ten-feature
```

---

## ✅ Best Practices cho Intern

### ✨ DOs (Nên làm)
- ✅ Luôn `git pull` trước khi `git push`
- ✅ Commit thường xuyên với message rõ ràng
- ✅ Sử dụng `git status` để kiểm tra trước mỗi hành động
- ✅ Tạo branch mới cho mỗi feature/bugfix
- ✅ Sử dụng `--rebase` để có history sạch

### ❌ DON'Ts (Không nên làm)
- ❌ Không bao giờ `git push --force` lên main/master
- ❌ Không commit trực tiếp lên main/master
- ❌ Không sử dụng `git reset --hard` nếu chưa chắc chắn
- ❌ Không merge branch chưa được review

---

## 🆘 Commands Cứu Hộ

### Khi làm sai
```bash
# Undo commit cuối (giữ lại changes)
git reset --soft HEAD~1

# Undo tất cả changes chưa commit
git checkout .

# Quay về trạng thái commit cụ thể
git checkout <commit-hash>
```

### Khi có conflict
```bash
# Hủy merge/rebase
git merge --abort
git rebase --abort

# Tiếp tục sau khi fix conflict
git add .
git merge --continue
git rebase --continue
```

---

## 📚 Tài Liệu Tham Khảo

- **Git Official Docs**: https://git-scm.com/docs
- **Interactive Git Tutorial**: https://learngitbranching.js.org/
- **Git Cheat Sheet**: https://training.github.com/downloads/github-git-cheat-sheet/

---

> **💡 Lưu ý**: Hãy luôn backup code quan trọng trước khi thực hiện các lệnh có thể làm mất dữ liệu!