# MUHAMAD SAID SABIK AL FAKIH
# 1. Menampilkan Nama Karyawan yang Berada di Departemen yang Dipimpin oleh Manajer dengan Nama 'Rika'
![1](https://github.com/Fakih1204/m-fakih-/assets/174295395/98b878d6-8ddc-44f3-850b-6a4f65938026)

SELECT k.nama
FROM Karyawan k
JOIN Departemen d ON k.id_dept = d.id_dept
WHERE d.manajer_nik = (SELECT nik FROM Karyawan WHERE nama = 'Rika');
# 2. Menampilkan Nama Proyek yang Dikerjakan oleh Karyawan dari Departemen 'RnD'
![2](https://github.com/Fakih1204/m-fakih-/assets/174295395/dd9376a2-915c-4ba5-b348-8fa2f9074186)

SELECT DISTINCT p.nama
FROM Project p
JOIN ProjectDetail pd ON p.id_proj = pd.id_proj
JOIN Karyawan k ON pd.nik = k.nik
JOIN Departemen d ON k.id_dept = d.id_dept
WHERE d.nama = 'RnD';
# 3. Menampilkan Nama Karyawan yang Terlibat dalam Lebih dari Satu Proyek
![3](https://github.com/Fakih1204/m-fakih-/assets/174295395/fe333021-0716-45eb-9ab2-08099d1c0215)

SELECT k.nama
FROM Karyawan k
JOIN ProjectDetail pd ON k.nik = pd.nik
GROUP BY k.nama
HAVING COUNT(pd.id_proj) > 1;

# 4. Menampilkan Nama Proyek yang Melibatkan Karyawan Terbanyak
![4](https://github.com/Fakih1204/m-fakih-/assets/174295395/c4c86232-0610-41f9-8620-b905b20deb11)

SELECT p.nama
FROM Project p
JOIN ProjectDetail pd ON p.id_proj = pd.id_proj
GROUP BY p.nama
ORDER BY COUNT(pd.nik) DESC
LIMIT 1;
# 5. Menampilkan Nama Proyek yang Diikuti oleh Karyawan dengan Gaji Pokok Kurang dari 3 Juta
![5](https://github.com/Fakih1204/m-fakih-/assets/174295395/8f6bcc31-f0ec-4db3-af51-16dd4a2a503b)
SELECT DISTINCT p.nama
FROM Project p
JOIN ProjectDetail pd ON p.id_proj = pd.id_proj
JOIN Karyawan k ON pd.nik = k.nik
WHERE k.gaji_pokok < 3000000;

