# quantization_code

## description

노션 개인 블로그의 quantization에 대한 코드입니다. 

각 .ipynb 파일들은 quantization의 을 numpy로 구현한 내용의 파일입니다.

- quantizatoin.ipynb : 기초적인 absmax quantization, zeropoint quantization에 관한 내용입니다.

- quantization_vector_wise_quantization.ipynb : matmul시에 발생하는 outlier의 범위를 제한하기 위해 고안된 quantization 기법입니다. input_x의 row 단위로 absmax를 추출하고 weight_w의 칼럼 단위로 absmax를 추출하고 각 행과 열 단위로 quantization을 한 후에 matmul을 합니다. dequantization시에는 각 행과 열의 absmax값들의 외적을 활용합니다.

- mixed_precision_decomposition.ipynb : vector-wise quantization 역시도 llm과 같은 거대 모델에서는 outlier로 인한 오차가 누적될 때 성능이 하락하는 문제가 있었기 때문에, outlier가 있는 행렬과 없는 행렬로 행렬을 분해한 후, outlier가 있는 행렬은 FP16으로 matmul 해주고, outlier가 없는 행렬은 vector-wise quantization을 해주는 코드입니다.
