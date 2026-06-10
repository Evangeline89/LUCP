
Project/
├── land_use_models/         
│   ├── tacnet.py             
│   ├── experiment.py         
│   ├── metrics.py            
│   ├── utils.py               
│   ├── base.py               
│   └── __init__.py
├── data_preprocessing/       
│   ├── prepare_datasets.py   
│   ├── nlcd_processor.py     
│   └── __init__.py
├── scripts/                  
│   ├── train_models.py       
│   └── test_models.py        
├── data/                      
├── requirements.txt
└── RUN_GUIDE.txt
```

## Environment configuration

```bash
# Python >= 3.9
pip install -r requirements.txt
```

## Data preparation

Place the NPZ formatted dataset in the `data/` directory. The dataset must contain the following fields:：

| 字段 | 形状 | 说明 |
|------|------|------|
| `lulc` | `(T, H, W)` | Land use type sequence |
| `drivers` | `(T-1, H, W, N)` | drivering factors |
| `classes` | `(C,)` | class code array |
| `class_names` | `(C,)` | class name |

run
```bash
python scripts/test_models.py --data data/jilin_real_v3.npz --model-dir artifacts/seeds --models tacnet --sequence-years 2019 2020 2021 2022 2023 --target-year 2024  --device cuda --output-dir results
```


## Evaluation indicators

- **Overall Accuracy (OA)** 
- **Kappa** — Cohen's Kappa 
- **Figure of Merit (FoM)** 
- **Change F1** 

## License

This project is for academic research use only.
