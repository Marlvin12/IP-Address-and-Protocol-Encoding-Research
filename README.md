# IP Address and Protocol Encoding Research

## Research Objective
Determine the optimal encoding techniques for IP addresses and protocol data across different machine learning algorithms for network security/classification tasks.

## Data Preparation
### Dataset Collection
- Gather network traffic data with diverse IP addresses and protocols
- Include both normal and anomalous traffic patterns
- Consider public datasets like UNSW-NB15, CIC-IDS2017, or CICIDS2018

### Data Preprocessing
- Clean data (remove duplicates, handle missing values)
- Extract IP addresses and protocols as separate features
- Split into training/validation/test sets (70/15/15)

## Encoding Techniques Implementation

### For IP Addresses:
1. **Decimal Conversion**
   - Convert each octet to decimal (e.g., 192.168.1.1 → [192, 168, 1, 1])
   - Normalize values (0-255 → 0-1)

2. **Zero-padded Concatenation**
   - Remove dots and ensure fixed-length (e.g., 192.168.1.1 → 192168001001)
   - Apply scaling/normalization

3. **One-hot Encoding**
   - Create binary vectors for each unique IP
   - Consider dimensionality reduction for large datasets

4. **Binary Representation**
   - Convert to 32-bit binary format
   - Treat each bit as a feature

5. **Geolocation Features**
   - Map IPs to countries, regions, ASNs
   - Generate categorical features based on geography

6. **Network-based Features**
   - Extract subnet information (Class A/B/C)
   - Calculate broadcast/network addresses
   - Identify internal vs. external addresses

### For Protocols:
1. **One-hot Encoding**
   - Binary vector for each protocol type

2. **Label Encoding**
   - Assign integer values to each protocol

3. **Target Encoding**
   - Replace protocol with average target value for that protocol

4. **Mean Encoding**
   - Replace with statistical measures from target variable
   
5. **Frequency Encoding**
   - Replace with frequency of occurrence

## Experimental Design
### Algorithm Selection
- Logistic Regression (baseline) using GLM.jl
- SVM (with different kernels) using LIBSVM.jl
- Neural Networks using Flux.jl (test different architectures)
- Random Forest (vary depth and estimators) using DecisionTree.jl
- Naive Bayes (Gaussian and Multinomial) using NaiveBayes.jl

### Hyperparameter Tuning
- Grid search for optimal parameters for each algorithm
- 5-fold cross-validation

### Evaluation Metrics
- Accuracy, Precision, Recall, F1-score
- ROC-AUC and PR-AUC curves
- Training and inference time
- Memory usage

## Implementation Plan
### Phase 1: Baseline Testing
- Implement all encoding techniques using Julia's type system
- Run quick tests with default parameters
- Identify promising combinations
- Use Julia's multiple dispatch for flexible algorithm implementation

### Phase 2: In-depth Analysis
- Focus on top-performing encoding-algorithm pairs
- Perform hyperparameter optimization
- Conduct statistical significance testing

### Phase 3: Ensemble Methods
- Test combinations of encoding techniques
- Build ensemble models using best performers

## Results Documentation
### Complete the Tables
- Fill in performance metrics for each cell
- Color-code by performance tier

### Visualization
- Create heatmaps of performance across techniques
- Plot learning curves for best combinations
- Generate ROC curves for comparison

### Analysis Report
- Document strengths/weaknesses of each approach
- Identify patterns in algorithm-encoding compatibility
- Provide recommendations based on use case

## Future Work
1. Investigate advanced encoding techniques (embeddings, etc.)
2. Test on different network environments (IoT, enterprise, etc.)
3. Consider computational efficiency for real-time applications

## Getting Started
```bash
# Clone the repository
git clone https://github.com/username/ip-encoding-research.git
cd ip-encoding-research

# Start Julia and activate the project
julia --project=.

# Install dependencies (from Julia REPL)
julia> import Pkg; Pkg.instantiate()

# Run baseline experiments
julia> include("src/run_baseline.jl")

# Generate visualizations
julia> include("src/generate_charts.jl")
```

## Project Structure
```
ip-encoding-research/
├── data/
│   ├── raw/              # Original datasets
│   └── processed/        # Preprocessed datasets
├── notebooks/            # Exploratory analysis Pluto notebooks
├── results/              # Results and visualizations
├── src/                  # Source code
│   ├── encoders/         # IP and protocol encoding implementations
│   ├── models/           # ML model implementations
│   └── utils/            # Helper functions
├── Project.toml          # Julia project dependencies
├── Manifest.toml         # Julia package versions
└── README.md             # This file
```

## License
This project is licensed under the MIT License 

## Contact
For any questions or suggestions, please open an issue or contact [marlvingore.edu@gmail.com].
