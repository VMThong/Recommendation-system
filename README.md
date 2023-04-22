# Recommendation-system

## Training Model.ipynb
+ Project này dùng để xây dựng một model dùng để recommendation 10 sản phẩm nhiều khả năng sẽ được người dùng tương tác 
    cho từng khách hàng trong số 22000 khách hàng với hơn 14000 loại sản phẩm.
+ Trong project có để cập đến hai loại model là MF (Matrix Factorization) và NeuMF (Neural Matrix Factorization) để sử dụng cho recommendation system
+ Sau khi model được train xong thì một số hàm sẽ được dùng để kiểm tra hiệu suất model như mean_precision_recall_at_k, average_ndcg, và hit_rate

## Negative Processing.ipynb
+ Vì sample cho recommendation system này chỉ gồm lịch sử các sản phẩm đã được khách hàng mua vậy nên rất khó để biết mức độ tương tác của khách hàng với sản phẩm
+ Do đó, project này sẽ dùng cách tạo mẫu âm (Negative Sampling) thường được dùng cho Implicit Feedback trong recommendation.
+ Do đó, mẫu dùng để training sẽ bao gồm hai nhãn là 1 (những sản phẩm đã được khách hàng mua trong quá khứ) và 0 (những sản phẩm chưa bao giờ được khách hàng mua)
+ Cách tạo mẫu âm được đề cập trong file này bao gồm: dựa theo điểm số tương tác của khách hàng với sản phẩm đó
+ Cơ chế lấy mẫu thì trước đó một mẫu training được tạo bằng phương pháp lấy mẫu ngẫu nhiên để tạo mẫu âm (gọi là mẫu 1) và sử dụng mẫu này cho Training Model.ipynb
+ Sau khi training mẫu này sẽ được dùng để predict score của 14000 sản phẩm cho từng khách hàng
+ Các sản phẩm với điểm số cao nhất sẽ được dùng cho mẫu 2, mục đích của việc này để giúp mô hình có thể phân biệt được sản phẩm nào mà người dùng đã tương tác và
  với những sản phẩm có khả năng cao mà người dùng sẽ tương tác.
+ Lý do có hai đoạn code để tạo mẫu âm là do trong đoạn code một thì mô hình sẽ dự đoán toàn bộ score cho 14000 sản phẩm và chọn ra số lượng mẫu âm có score cao nhất
  và không trùng với sản phẩm khách hàng đã mua. Việc này tốn rất nhiều thời gian để tạo mẫu (hơn 6 tiếng), do đó code tạo mẫu thứ hai chỉ lấy ngẫu nhiên một lượng sản
  phẩm trong 14000 sản phẩm để cho vào mô hình và dự đoán score. Việc này giúp rút ngắng thời gian tạo mẫu xuống còn 2 tiếng.
+ Sau đó mẫu sẽ được cho vào một file csv và đưa vào Training Model.ipynb để tiến hành training.
