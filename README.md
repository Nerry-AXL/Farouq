# Cryptographic Algorithm Performance Analysis

A comprehensive benchmarking project that compares the efficiency and resource usage of four different cryptographic algorithms across various file sizes and processing loops.

## 📋 Project Overview

This project systematically evaluates the performance characteristics of four widely-used cryptographic algorithms:
- **AES** (Advanced Encryption Standard)
- **Blowfish**
- **ChaCha20**
- **ECC** (Elliptic Curve Cryptography)

The analysis provides quantitative data on CPU usage, memory consumption, processing time, and encrypted file sizes to help developers and system architects make informed decisions about algorithm selection.

## 🏗️ Project Structure

```
cryptographic-algorithm-analysis/
├── analysis.ipynb                           # Main analysis notebook
├── file_size comparative analysis graph.png  # Generated visualization
├── Loop_count comparative analysis graph.png # Generated visualization
├── AESRESULT/                               # AES algorithm results
│   ├── 100K_READING/
│   │   ├── 50LOOPS/
│   │   ├── 75LOOPS/
│   │   ├── 100LOOPS/
│   │   └── 125LOOPS/
│   ├── 500KB_READING/
│   ├── 1MB_READING/
│   ├── 2MB_READING/
│   └── 3MB_READING/
├── BLOWFISHRESULT/                          # Blowfish algorithm results
├── CHACHA20RESULT/                          # ChaCha20 algorithm results
└── ECCRESULT/                               # ECC algorithm results
```

Each algorithm directory contains subdirectories for different file sizes, with further subdirectories for different loop counts, each containing 4 trial CSV files.

## 🔬 Experimental Design

### Test Parameters

| Parameter | Values |
|-----------|--------|
| **File Sizes** | 100KB, 500KB, 1MB, 2MB, 3MB |
| **Loop Counts** | 50, 75, 100, 125 iterations |
| **Trials** | 4 separate test runs per combination |
| **Operations** | Encryption and Decryption |

### Metrics Collected

For each test iteration, the following metrics are recorded:

| Metric | Description | Unit |
|--------|-------------|------|
| `cpu_percent` | CPU utilization during operation | Percentage (%) |
| `memory_used_mb` | Memory consumption | Megabytes (MB) |
| `process_time_sec` | Time taken for encryption/decryption | Seconds (sec) |
| `encrypted_size_bytes` | Size of encrypted output | Bytes |

## 📊 Data Structure

Each CSV file contains the following columns:
- `operation`: Type of operation (encryption/decryption)
- `iteration_number`: Iteration within the loop (1-100)
- `file_size_label`: Human-readable file size description
- `cpu_percent`: CPU usage percentage
- `memory_used_mb`: Memory usage in MB
- `process_time_sec`: Processing time in seconds
- `encrypted_size_bytes`: Size of encrypted data in bytes

## 🔍 Analysis Methodology

The analysis notebook (`analysis.ipynb`) performs the following steps:

1. **Data Collection**: Recursively finds and loads all CSV files
2. **Metadata Extraction**: Parses algorithm, file size, loop count, and trial information from file paths
3. **Data Consolidation**: Combines all data into a single DataFrame
4. **Statistical Analysis**: Calculates mean, standard deviation, min, and max values
5. **Visualization**: Generates comparative charts and graphs

## 📈 Key Findings

### Performance Rankings

Based on comprehensive analysis across all metrics:

1. **🥇 CHACHA20** - Fastest and most CPU-efficient
2. **🥈 AES** - Competitive performance with lower memory usage
3. **🥉 BLOWFISH** - Good performance for smaller files
4. **4️⃣ ECC** - Slowest and most resource-intensive

### Detailed Insights

#### Speed Performance
- **CHACHA20** consistently achieves the fastest processing times across all file sizes
- **AES** shows competitive performance, especially for medium file sizes
- **BLOWFISH** performs well with smaller files but degrades with larger ones
- **ECC** is significantly slower, with performance degrading as file size increases

#### CPU Efficiency
- **CHACHA20** uses the least CPU resources across all file sizes
- **AES** shows excellent CPU efficiency for medium files
- **BLOWFISH** shows good CPU efficiency for smaller files
- **ECC** requires the highest CPU usage, especially for larger files

#### Memory Usage
- **AES** typically uses the least memory
- **CHACHA20** shows good memory efficiency
- **BLOWFISH** has moderate memory usage
- **ECC** consumes the most memory resources

#### Scalability
- **CHACHA20** maintains consistent performance across all file sizes
- **AES** shows consistent performance with good memory efficiency
- **BLOWFISH** performance degrades more noticeably with larger files
- **ECC** shows the most dramatic performance degradation with larger files

## 🛠️ Usage Instructions

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Running the Analysis

1. **Clone or download** the project files
2. **Navigate** to the project directory
3. **Launch Jupyter Notebook**:
   ```bash
   jupyter notebook analysis.ipynb
   ```
4. **Run all cells** to perform the complete analysis

### Understanding the Results

The notebook generates:
- **Summary statistics** for each algorithm across all test conditions
- **Comparative visualizations** showing performance differences
- **Ranking tables** for each metric and file size combination
- **Statistical insights** with detailed explanations

## 📊 Generated Visualizations

The analysis produces several types of visualizations:

1. **Performance Comparison Charts**: Bar charts comparing algorithms across different metrics
2. **File Size Analysis**: Performance trends as file size increases
3. **Loop Count Analysis**: Impact of iteration count on performance
4. **Statistical Summaries**: Mean, standard deviation, and range analysis

## 🎯 Practical Applications

This benchmarking data is valuable for:

- **System Architects**: Choosing appropriate encryption algorithms for specific use cases
- **Performance Optimization**: Making informed decisions about cryptographic implementations
- **Resource Planning**: Estimating hardware requirements for encryption-heavy applications
- **Academic Research**: Supporting cryptographic performance analysis studies
- **Development Teams**: Selecting algorithms based on performance requirements

## 📋 Algorithm Recommendations

### For Speed-Critical Applications
- **Primary Choice**: CHACHA20
- **Alternative**: AES (for medium files)

### For Memory-Constrained Systems
- **Primary Choice**: AES
- **Alternative**: CHACHA20 (good balance of speed and memory)

### For High-Security Requirements
- **Primary Choice**: AES or ECC (depending on specific security needs)
- **Note**: ECC provides strong security but at significant performance cost

### For General-Purpose Applications
- **Primary Choice**: CHACHA20 (best overall performance)
- **Alternative**: AES (if memory efficiency is important)

### For Small File Processing
- **Primary Choice**: BLOWFISH or CHACHA20
- **Alternative**: AES (consistent performance)

## 🔬 Methodology Notes

- **Test Environment**: All tests conducted on the same hardware to ensure fair comparison
- **Statistical Rigor**: Multiple trials (4 per condition) to account for system variability
- **Comprehensive Coverage**: Tests span realistic file sizes and processing loads
- **Reproducible Results**: All data and analysis code included for verification

## 📄 License

This project is provided for educational and research purposes. Please ensure compliance with relevant cryptographic export regulations in your jurisdiction.

## 🤝 Contributing

Contributions to improve the analysis methodology, add new algorithms, or enhance visualizations are welcome. Please ensure any additions maintain the same level of statistical rigor and comprehensive testing.

---

**Note**: This analysis focuses on performance characteristics. Security considerations, regulatory compliance, and specific use case requirements should also be evaluated when selecting cryptographic algorithms for production systems. 