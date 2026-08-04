# Implementation and Analysis of Selection Algorithms
This repository contains implementations, performance analyses, and an empirical benchmarking suite for two linear-time selection algorithms:
1. **Deterministic Selection** using Median of Medians (Worst-Case O(n))
2. **Randomized Selection** using Quickselect (Expected O(n))

Both implementations utilize **3-Way Dutch National Flag Partitioning** (`< pivot`, `== pivot`, `> pivot`) to handle duplicate elements efficiently and prevent infinite recursion or performance degradation.

## Project Structure
•	MSCS-532_Project_Phase3_Step1.ipynb  # Source code for algorithms, benchmarks, and plot generation
•	Step1_Documentation # Project documentation 
•	Step1_README.md                # Summary of findings
Environment Requirements
•	Python 3.8+
•	matplotlib ( recommended for generating visual comparison plots)

What Execution Does:
  1.	Validates algorithm correctness across unit test cases.
  2.	Runs timing benchmarks across 6 array sizes (N {1000,5000,10000,50000,100000,200000}) across 4 input distributions (Random, Sorted, Reverse-Sorted, High Duplicates).
  3.	Prints structured execution timetables (in milliseconds) and overhead ratios to the terminal.
  4.	Generates and saves a 4-panel visual comparison chart as selection_empirical_analysis.png if matplotlib is installed.
   
Summary of Findings
  1. Linear Time Scaling (O(n))
  Across Random, Sorted, and Reverse-Sorted data distributions, doubling the input size N roughly doubles execution time for both algorithms. This empirically confirms that both Deterministic Selection and Randomized Quickselect scale linearly as predicted by theoretical O(n) bounds.
  2. Lower Constant-Factor Overhead in Randomized Selection
  For unique element distributions (Random, Sorted, Reverse-Sorted), Randomized Quickselect is consistently 1.14 x to 1.99 x faster than Deterministic Median of Medians. This confirms that selecting a random pivot carries significantly lower overhead ((c)) than Median of Medians, which incurs extra computational cost by creating sub-arrays and recursively extracting group medians.
  3. Immunity to Input Distribution
  Randomized Quickselect showed nearly identical performance on Sorted (~42.9 ms at N = 100k and Reverse-Sorted data (~46.3 ms at N = 100k) compared to Random data (~46.3 ms at N = 100k ). Selecting a pivot uniformly at random eliminates the sensitivity to pre-sorted arrays that plagues standard deterministic partitioning algorithms.
  4. High-Duplicate Efficiency Shift
  On the High Duplicates distribution (values between 0 and 10), the 3-Way Dutch National Flag partitioning drastically reduced execution time for both algorithms. Interestingly, Deterministic Selection outperformed Randomized Selection by a factor of 0.72 x to 0.085 x on large duplicate arrays. Because value frequencies are high, the Median of Medians calculation consistently targets the most frequent median element, allowing 3-way partitioning to isolate and collapse massive blocks of equal elements in a single pass.
  

