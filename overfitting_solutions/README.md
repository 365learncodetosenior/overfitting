# Thi nghiem khac phuc overfitting

Thu muc nay dung de minh hoa overfitting tren bo du lieu `Gia_Nha_Ha_Noi.csv`.

## Chay

Mo PowerShell tai thu muc goc cua project va chay bang moi truong sach:

```powershell
.\.venv_run\Scripts\Activate.ps1
python .\overfitting_solutions\overfitting_demo.py
```

Moi truong `.venv_run` duoc tao de tranh loi DLL cua `.venv` cu. Neu chua co,
tao va cai thu vien bang lenh:

```powershell
py -m venv .venv_run
.\.venv_run\Scripts\python.exe -m pip install numpy scipy scikit-learn pandas matplotlib
```

Ket qua duoc tao trong `overfitting_solutions/outputs/`:

- `model_results.csv`: diem R2 train/test, khoang cach train-test, MAE va RMSE.
- `overfitting_comparison.png`: bieu do so sanh cac mo hinh.

## Mo hinh duoc so sanh

1. **Da thuc bac 8 + LinearRegression**: mo hinh co do phuc tap cao de tao tinh huong overfitting. Dau hieu la `R2_train` rat cao nhung `R2_test` thap hon ro ret.
2. **Da thuc bac 2**: giam do phuc tap, giam kha nang hoc ca nhieu ngau nhien.
3. **Ridge**: them phat tang L2, lam cac he so lon bi co lai va giup mo hinh on dinh hon.
4. **Lasso**: them phat tang L1, co the dua mot so he so ve 0 va loai bot dac trung it huu ich.
5. **Ridge + GridSearchCV**: tu dong chon bac da thuc va `alpha` bang cross-validation thay vi chon bang cam tinh.

Tat ca tien xu ly nam trong `Pipeline`, vi vay cac tham so scale va ma hoa chi duoc hoc tren moi fold/tap train, tranh data leakage.

## Cach ket luan

- Uu tien mo hinh co `RMSE_test` thap va `R2_test` cao.
- `Khoang_cach_R2` lon la canh bao overfitting.
- Khong dung `R2_train` mot minh de ket luan mo hinh tot.

`.venv` cu bi loi `DLL load failed` khi nap cac file native cua SciPy. Hay dung
`.venv_run` theo huong dan tren thay vi tiep tuc dung moi truong cu.
