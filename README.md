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
## Problems
- Pengiriman yang terlambat lebih banyak dibandingkan yang tepat waktu
- Jika ini berlangsung lama, kemungkinan customer berpindah ke lain E-Commerce lebih besar
## Tujuan Pembuatan Model
- Memprediksi pengiriman yang akan mengalami keterlambatan
- Memberikan treatment kepada customer yang terprediksi pengirimannya akan terlambat
# Beberapa Insight dari Data
1. Pengiriman paling banyak dilakukan dari gudang F
2. Pengiriman yang terlambat ternyata banyak datang dari barang yang tidak terlalu berat
3. Pengiriman yang terlambat banyak datang dari product importance _low_
# ML Modeling
