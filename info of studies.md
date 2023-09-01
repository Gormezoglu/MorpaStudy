# RATIONALE

- Our data is highly imbalanced. So we should use AUCPR (Area under Curve Precision Recall) as metric. (Precision-Recall is a useful measure of success of prediction when the classes are very imbalanced. source:scikit-learn.org)
- We should use XGB as model.
- We should use RF as alternative model.
- We should use SVM as another alternative model (with SMOTE).
- We should use GridSearch to find best parameters.

# SHOULD WE USE SMOTE?

- SMOTE is used to balance the data. But it is not necessary to use it. We can use it with XGB and RF. But we should not use it with SVM. Because SVM is a linear model and not good with imbalanced data.

# REASONING

- For the nature of the problem, our minority class is not meant to be incorrectly represented. Tis is the real-world distribution. GTS must be rare compared to Non-GTS
- Our dataset also has data quality issues. Since we labeled GTS with our own assumptions, generating synthetic data will not help us to improve the model performance.

# TAKEN FEATURES FOR ML MODELS

  I will select the variables where fraud class have a interesting behavior and might can help us predict
  df = df[['Sınav Türü',"Puan","S_süre","Sınıf","Ders","Aktif Materyal Sayısı","total_study_time","Label"]]

---

## 0_table_population

- this helps to populate the table. Don't need to run over and over.

## 0_data_analysis

- The most promising outcome of what I have so far. Could be used as base study for enhacement.
  validation_0-aucpr:0.27762 | 0 false positive | 2 true positive | 100% accuracy

## t0_v3

- validation_0-aucpr:0.28950 | 3 False Positive

## t0_v4_XGB_roc_auc_base (t6 is used aucpr instead of auc)

- AUC used for evaluation metric but since our data is imbalanced, we should use AUCPR instead. So this is not a good model.

## t1_v4_SMOTE&RF

- This has different analysis appraoch. I used SMOTE to balance the data and then used RF to train the model. The outputs seem good visually. Can be used for UI
- #LOOKING THE V's KISMINI BASE ÇALIŞMAYA EKLE. BURADAN DAĞILIMLARI FARKLI OLAN FEATURE'LARI ALMAMIZ GEREKTİĞİNİ İFADE ET. BENZER DAĞILIM GÖSTEREN FEATURELAR ANLAMLI BİR VERİ SAĞLAMAYACAĞINI BELİRT.

## t2_v4_SMOTE&XGB

- This is similar with t1_v4_SMOTE&RF but used XGB instead of RF. The outputs seem good visually. Can be used for UI

## t3_v4_XGB_süre adjusted

- t0_v4_XGB_roc_auc_base with time adjusted. AUC doesn't help but SMOTE can be tried with AUCPR. !!!

## t4_v4_XGV_reorganizing

- Still uses AUC as metric but reorganized the code. Can be edited for AUCPR.

# TODO:

- Erkan hocanın önerilerini dikkate alarak yeni bir versiyon çalıştır.

  - Soru üzerinde geçen süre ile bir bilgiye ulaşmak ( morpa datasında soru üzerinde geçen süre verisi yok.)
  - Sınav tahmini için eski kaynaklar üzerinden çıkarımlarda bulun (Bunu tam anlamadım ancak ilgili sınav konularına ait kaynaklar verisi incelenerek bir yöntem oluşturulabilir. - Yapıldı)
  - XGBOOST yaparken: [gaming the system yapıldığını tahmin ettiğimiz parametreleri analizi yaparken çıkarmak gerekir.]
    - üye bilgisini çıkar.
    - Giriş timestamp'ini çıkar.
    - Giriş Log çıkar
    - Kategorikleri çıkarıp tekrar bak (bunu hem kategorikleri çıkararak hem de çıkarmadan iki versiyon bakılabilir.)

- Yukarıda AUC ile yapılan analizlerin hepsini AUCPR ile yap ve sonuçları karşılaştır.
- Sonrasında bunları bir rapor haline getirerek Erkan hocaya ilet.
- Gelecek Feedback'e göre ilerle.

---

## t5 is started

- This resulted 1 False Positive. Not better than base model.
  - Taken the features suggested by Erkan hoca - (Sınav Türü, Puan, S_süre, Sınıf, Ders, Aktif Materyal Sayısı, total_study_time) Extracted Üye, Sınav, Konu and Giriş Log from the data. 
  - t6'nın altındaki GridSearch'ı buraya al
  - max(AUCPR) = 0.26703 | 4 False Positive | 50% accuracy

## t6_v4_XGB_roc_aucpr_base - (modified t0_v4)

- It has GridSearchCV definitions under this version. It can be used in Base Scenario for give more information
- This is modified version of t0_v4_XGB_roc_auc_base. AUCPR is used as metric.
  - max(AUCPR) = 0.21395 | 3 False Positive | 40% accuracy

## t7_v4_SMOTE&RF - (modified t1)

- Modified t1 
  - Extracted GridSearchCV
-14 true positive | 55 false positive | 0% accuracy 
