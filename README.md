# E-Commerce Shipping Analyst Classification: Project Overview
- Membangun model yang membantu perusahaan memprediksi suatu pengiriman barang akan mengalami keterlambatan atau tidak
- Data di dapat dari [E-Commerce Shipping Data|Kaggle](https://www.kaggle.com/datasets/prachi13/customer-analytics/code)
- Menghandle data Outlier yaitu fitur _prior_purhases_ dan _weight_in_gms_ dengan metode `Zscore`
- Menghandle data imbalance dengan metode `over sampling`
- Split data menjadi _data train_ dan _data_test_
- Transformasi Distribusi:
  - Fitur _weight_in_gms dan _prior_purchases_ dengan metode `np.sqrt`
  - Fitur _discount_offered_ dengan metode `inverse (1/median if x==0)`
- Melakukan `Label Encoder` untuk fitur _gender_ dan `One Hot Encoding` untuk fitur kategorik sisanya
- Melatih model dengan berbagai model dari `Xgboost` ,`Stacking`, dan `Bagging`
- Validasi model dengan _data_test_

## Permasalahan
- Pengiriman yang terlambat lebih banyak dibandingkan yang tepat waktu
- Jika ini berlangsung lama, kemungkinan customer berpindah ke lain E-Commerce lebih besar

## Tujuan Pembuatan Model
- Memprediksi pengiriman yang akan mengalami keterlambatan
- Memberikan treatment kepada customer yang terprediksi pengirimannya akan terlambat

# Beberapa Insight dari Data
1. Pengiriman paling banyak dilakukan dari gudang F dan dengan metode pengiriman menggunakan kapal(ship)
![warehouse](https://user-images.githubusercontent.com/99067834/162570252-c6780574-1c3e-4a06-bc55-b28c59e5ccc3.png)
2. Pengiriman yang terlambat ternyata banyak datang dari barang yang tidak terlalu berat
![weight in grams](https://user-images.githubusercontent.com/99067834/162569843-71c46878-b50b-4ae7-b384-4ac41bc7cb7e.png)
3. Pengiriman yang terlambat banyak datang dari product importance _low_
![product importance](https://user-images.githubusercontent.com/99067834/162569857-c76ef9d1-051f-4d5e-8c21-fc74a784e57e.png)

# ML Modeling
Sebelum melatih model, kita membagi datanya terlebih dahulu menjadi test set(20%) dan train set (80%). Kemudian kita latih modelnya ke beberapa algoritma dan melakukan evaluasi menggunakan metric `Recall`. Alasannya adalah untuk meminimalisir __False Negatif__, karena fokus kita adalah memprediksi pengiriman yang terlambat dan segera memberikan treatment kepada customer yang pengirimannya di prediksi akan mengalami keterlambatan. Algoritma yang kita gunakan untuk melatih model antara lain :
- XGBoost RFClassifier
- Logistic Regression
- Gausian NB
- Decission Tree
- Random Forest
- Bagging Classifier

# Evaluasi Model
Melalui beberapa tahapan model selection, akhirnya `XGBoost RFClassifier` dipilih sebagai algoritma dari model yang akan kami buat dengan `Recall` yakni 0.75 untuk late delivery dan 0.53 untuk on-time delivery
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
</head>
<body>
 
 <table>
 	<tr>
 		<td> Prediction</td>
 		<td> Precision</td>
    <td> Recall</td>
    <td> F1-Score</td>
 	</tr>
 	<tr>
 		<td> Late</td>
 		<td> 0.68</td>
    <td> 0.75</td>
    <td> 0.71</td>
 	</tr>
  <tr>
 		<td> On Time</td>
 		<td> 0.61</td>
    <td> 0.53</td>
    <td> 0.57</td>
 	</tr>
 </table>

</body>
</html>

# Rekomendasi Bisnis
1. Melakukan perbaikan manajemen distribusi barang:
  - Mode of shipment: jangan terlalu banyak menggunakan moda kapal (ship) → buat rekomendasi mode of shipment di checkout page.
  - Warehouse: warehouse block F meng-handle terlalu banyak barang, oleh karena itu perlu dilakukan pengaturan agar distribusi barang antar warehouse menjadi lebih merata.
2. Melakukan beberapa improvement untuk meningkatkan customer retention rate:
  - Melakukan dual-late redefinition
  - Memberikan kupon partial refund ongkos kirim atau diskon untuk pembelian selanjutnya

## Sekilas Mengenai Dual-Late Redefinition
Membuat standar atau batas keterlambatan yang berbeda antara pihak logistik dan pihak pelanggan
![Picture1](https://user-images.githubusercontent.com/99067834/162573778-2b397376-3633-4ec9-83b8-2e3ea5f332ff.png)

# Tim Di Balik Pembuatan Project
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
</head>
<body>
 
 <table>
 	<tr>
 		<td> Member</td>
 		<td> Email</td>
    <td> LinkedIn Url</td>
 	</tr>
 	<tr>
 		<td> Our Mentor : Muhammad Mirza Fahmi</td>
 		<td> mmirzafahmi@hotmail.com</td>
    <td> https://www.linkedin.com/in/mmirzafahmi/</td>
 	</tr>
  <tr>
 		<td> Our Leader : Fakhri Nurrahmadi</td>
 		<td> fnurrahmadi@gmail.com</td>
    <td> https://www.linkedin.com/in/fnurrahmadi/</td>
 	</tr>
  <tr>
 		<td> Muhammad Iqbal Tawakkal</td>
 		<td> nurmengard587@gmail.com</td>
    <td> https://www.linkedin.com/in/mit23/</td>
 	</tr>
  <tr>
 		<td> Ryan Rizky Fathinanto</td>
 		<td> ryanrizkyf@gmail.com</td>
    <td> https://www.linkedin.com/in/ryanrizkyf/</td>
 	</tr>
  <tr>
 		<td> Dyah Phitaloka</td>
 		<td> Dyahphitaloka09@gmail.com</td>
    <td> https://www.linkedin.com/in/dyah-phitaloka/</td>
 	</tr>
  <tr>
 		<td> Dwi Muhammad Nurafli (Me)</td>
 		<td> dwirafli13@gmail.com</td>
    <td> https://www.linkedin.com/in/dwi-muhammad-nurafli-ba0a60168/</td>
 	</tr>
 </table>

</body>
</html>
