## 0_table_population

- this helps to populate the table. Don't need to run over and over.

## 0_data_analysis

- The most promising outcome of what I have so far. Could be used as base study for enhacement.
  validation_0-aucpr:0.27762

## t0_v3

- validation_0-aucpr:0.23937

## t0_v4_XGB_roc_auc_base

- AUC used for evaluation metric but since our data is imbalanced, we should use AUCPR instead. So this is not a good model.

## t1_v4_SMOTE&RF

- This has different analysis appraoch. I used SMOTE to balance the data and then used RF to train the model. The outputs seem good visually. Can be used for UI

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
-----------------------

## t5 is started
- This resulted 1 False Positive. Not better than base model. 
  - (Puan eklendi - Tekrar Çalıştır.)
  - t6'nın altındaki GridSearch'ı buraya al

## t6_v4_XGB_roc_aucpr_base - (modified t1)
- This is modified version of t0_v4_XGB_roc_auc_base. AUCPR is used as metric. 



