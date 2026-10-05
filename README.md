BAI 1: KHAO SAT FHS VA PHAN QUYEN FILE/FOLDER NANG CAO

MUC TIEU
- Thanh thao tao lap thu muc va dieu huong trong cay thu muc Linux FHS.
- Hieu va ap dung co che phan quyen bang so (octal) va bang ky tu (symbolic).
- Nam ro cach thay doi quyen so huu tep tin va nhom so huu.

BOI CANH
Trien khai thu muc dung chung cho ung dung web tai /var/www/my-app.
- public: chua trang tinh cong khai.
- logs: chua nhat ky he thong bao mat.


1. TAO CAU TRUC THU MUC

Lenh thuc hien:

```bash
sudo mkdir -p /var/www/my-app/public
sudo mkdir -p /var/www/my-app/logs
```

Ket qua:
- Tao thanh cong 2 thu muc /var/www/my-app/public va /var/www/my-app/logs.


2. PHAN QUYEN CHO THU MUC PUBLIC (750)

Yeu cau: Owner doc/ghi/thuc thi, Group chi doc/thuc thi, Others khong co quyen.

Lenh thuc hien:

```bash
sudo chmod 750 /var/www/my-app/public
```

Giai thich:
- 7 = rwx (Owner: toan quyen)
- 5 = r-x (Group: doc + thuc thi)
- 0 = --- (Others: khong co quyen)


3. PHAN QUYEN CHO THU MUC LOGS (770)

Yeu cau: Owner va Group toan quyen, Others khong co quyen.

Lenh thuc hien:

```bash
sudo chmod 770 /var/www/my-app/logs
```

Giai thich:
- 7 = rwx (Owner: toan quyen)
- 7 = rwx (Group: toan quyen)
- 0 = --- (Others: khong co quyen)


4. THAY DOI CHU SO HUU (CHOWN)

Gan Owner la user hien tai, Group la www-data:

```bash
sudo chown -R $USER:www-data /var/www/my-app
```


5. KIEM TRA KET QUA

Lenh kiem tra:

```bash
ls -la /var/www/my-app
```

Ket qua dau ra:

```
total 16
drwxr-xr-x 4 ubuntu www-data 4096 Oct  5 08:30 .
drwxr-xr-x 3 root   root     4096 Oct  5 08:30 ..
drwxrwx--- 2 ubuntu www-data 4096 Oct  5 08:30 logs
drwxr-x--- 2 ubuntu www-data 4096 Oct  5 08:30 public
```

Xac nhan:
- /var/www/my-app/public: drwxr-x--- (750) - Owner: ubuntu, Group: www-data.
- /var/www/my-app/logs:   drwxrwx--- (770) - Owner: ubuntu, Group: www-data.
- Phan quyen dung voi yeu cau de bai.


6. TONG KET CAC LENH DA THUC HIEN

```bash
sudo mkdir -p /var/www/my-app/public
sudo mkdir -p /var/www/my-app/logs
sudo chmod 750 /var/www/my-app/public
sudo chmod 770 /var/www/my-app/logs
sudo chown -R $USER:www-data /var/www/my-app
ls -la /var/www/my-app
```
