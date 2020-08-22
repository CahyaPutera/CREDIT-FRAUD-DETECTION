## Tugas IYKRA Data MBA.

# TRANSACTION DATA (CREDIT FRAUD)

“Data Transactions” (transactions.csv) - Fix dataset digunakan untuk usecase fraud dan clustering.

Sumber dataset : https://drive.google.com/file/d/1sr0k8_k7huFuHiR_C5P_r60VaBDzwoTb/view

Proses Classification Machine Learning terhadap data transaction.csv. 

Notebook EDA berisi mengenai tahap eksplorasi data, namun juga akan mencakup preprocessing. Sehingga setiap feature dari data yang di eksplorasi akan bersih dari Null Values, serta sesuai dengan definisi dari tiap features. Tujuan eksplorasi data ini adalah untuk mengetahui lebih lanjut pola dari customer yang melakukan fraud. 

Eksplorasi data di lakukan dalam beberapa tahap dan di lakukan berdasarkan kelompok data. Eksplorasi awal ke target features - isFraud, lalu eksplorasi ke kelompok numerical, categorical dan terakhir ekplorasi ke features datetime.

Notebook selanjutnya dalam rangka proses Machine Learning, terdiri dari HYPERPARAMETER Tuning dan MACHINE LEARNING nya itu sendiri. Sehingga dalam prakteknya, proses ini hanya terfokus untuk membangun model prediksi. Model yang di gunakan dalam pengujian adalah LogisticRegression dan KNNeighbors. Pembuatan model di lakukan dengan melalui metode pipelining, sehingga hasilnya juga akan cenderung lebih baik. Pembuatan model juga melewati beberapa tahap feature engineering, dimana dalam tahap ini, data akan di lakukan uji normalitas dan outliers checking, feature selection, dan cross-validation. Dan karena data sangat imbalanced, maka di lakukan oversampling dengan metode SMOTE.


# FEATURE DESCRIPTION :

- accountNumber             = The account number of The customer
- customerId    =  The ID of The customer
- creditLimit               =  The amount of money that can be charged to The debit card
- availableMoney        = The amount of money in The debit card before adjusting for pending charges      
- transactionDateTime       = The transaction timestamp when it happened
- transactionAmount        = The amount of transaction 
- merchantName          = The merchant name of The particular transaction
- acqCountry             = The country where The merchant is located
- merchantCountryCode    = The country code for The specific merchant
- posEntryMode        = a code that tells The processor how The transaction was captured
- posConditionCode   = a code identifying transaction conditions at The point-of-sale or point-of-service
- merchantCategoryCode    = The merchant category/types
- currentExpDate       =  The expiry date of The credit card
- accountOpenDate      = The date when The customer open The credit card
- dateOfLastAddressChange    = The last date when The customer change The credit card address
- cardCVV = The actual card verification value
- enteredCVV       = The entered card verification value
- cardLast4Digits     = The last 4 digits of The debit card
- transactionType        = The types of transactions
- isFraud      = The status of The fraud transaction
- echoBuffer    = number of delayed response transactions
- currentBalance =  The current balance of The debit card
- merchantCity = The location for The specific merchant (City)
- merchantState   = The location for The specific merchant (State)
- merchantZip = The location for The specific merchant (Zip Code)           
- cardPresent =     The physical presence of The debit card in The transaction
- posOnPremises = The location of The point of sales          
- recurringAuthInd  = wheTher The auThentication recurred or not
- expirationDateKeyInMatch = The match between The expiration date in The system and what was inputted

# SUMMARY - EDA 

Walaupun lumayan sulit untuk mengetahui atau mendapatkan pola dari customer yang fraud, kita dapat ketahui bahwa ada sekitar 10.892 customer atau sekitar 2% dari total seluruh customer yang tercatat sebagai fraud. Kita juga mengetahui bahwa fraud terjadi hampir merata di setiap hari, setiap tahun jumlahnya terus meningkat. Dan jika kita lihat porsi peritungan per bulannya, kita akan temukan bahwa ada sedikit peningkatan pada bulan Maret dan Oktober walaupun tidak terlalu signifikan.

Para customer yang fraud sering berbelanja pada merchant yang memiliki kategori online retail, fastfood atau makanan lainnya, sebagian besar dari merchant tersebut berasal dari US. Tipe transaksi yang banyak di lakukan pada adalah PURCHASE atau pembelian. Dan sebagian besar dari mereka yang fraud tidak membawa debit card, serta tidak memiliki kesamaan tanggal expiration yang tercatat dalam system dan yang di input.

Melalui pairplot() terlihat memang terdapat features yang memiliki persebaran cukup berpola, walaupun pola persebarannya sulit di lihat, tetapi jika diperhatikan dengan seksama, kita akan menemukan pola persebaran dimana pada customer yang fraud kebanyakan sebaran credit limitnya masih di kisaran 20.000 dollar atau lebih rendah lagi, sementara mereka yang tidak fraud berada di kisaran 30.000 sampai 50.000 dollar. Terlihat juga pada customer yang fraud, mereka memiliki credit limit dan available money yang cenderung lebih sedikit dibandingkan mereka yang tidak fraud.

# SUMMARY - MACHINE LEARNING

Setelah dilakukan oversampling, memang jelas tampak bahwa model menjadi lebih baik daripada sebelumnya. Dan pada akhirnya, model Logistic Regression dengan scaling menggunakan Robust Scaler dan teknik oversampling dengan SMOTE menjadi model yang paling baik untuk digunakan dalam memprediksi dataset ini.

Pada intinya, model ini memiliki 81% accuracy, serta 99% precision pada kategori yang tidak fraud. Terlebih lagi, model ini juga memiliki recall yang cukup tinggi pada kategori yang tidak fraud, model dapat memprediksi dengan benar sekitar 82% pada kategori ini, walaupun pada kategori yang fraud masih hanya sekitar 42%. Tetapi bagaimanapun juga versi model ini sudah lebih baik dan seimbang di bandingkan dengan versi sebelum di lakukan balancing.

# CHALLENGES 

- Size dataset yang tergolong besar, lebih dari 600.000 data. Sehingga processing datanya memakan waktu yang cukup lama. 
- Tuning Hyperparameter membutuhkan waktu sekitar 5 jam. Fitting model ke training data membutuhkan waktu sekitar 30 menit.
- Data sangat tidak seimbang (imbalanced) dengan jumlah rasio 98 : 2. Tentu saja ini menyulitkan dalam mencari pola dalam EDA dan modelling dalam MACHINE LEARNING.
- Keterangan definisi dalam beberapa feature belum jelas.
