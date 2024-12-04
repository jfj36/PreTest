
Pre-Test SOLUTION

1) Modify the package in order to make "test_cm.py" run successfully.
   [20]

    The issue was that the export_to_csv function was not defined in the module dataframe_builder. Therefore, it cannot be import from this module. 
    To make test_cm.py run succesfully I changed the __init__.py file by importing the export_to_csv function from the module data_exporter.
   
2) Try and understand what the function define_dataframe_structure()
    does and write an appropriate, human-readable, docstring for it.
    [10]

    The `define_dataframe_structure` function is used to define the structure of a DataFrame based on the column specifications provided. It takes a list of dictionaries as input, where each dictionary represents a column in the DataFrame. Each dictionary contains the keys 'name' and 'reps'. 

    The function creates a DataFrame with the following structure:
    - The column names in the DataFrame correspond to the values associated with the 'name' key in each dictionary.
    - The number of rows in the DataFrame is equal to the length of the list of representative points in the dictionary with the largest number of representative points.
    - The values in each column are the representative points in the list associated with the 'reps' key in each dictionary. If the list of representative points is shorter than the list with the largest number of representative points, the remaining values in the column are filled with NaN.

    The function iterates over the column specifications, finds the maximum length of representative points, and extends the numerical columns with NaN values to match the maximum length. Finally, it returns the DataFrame with the defined structure.


3) Try and understand what the function simulate_data() does and
    write an appropriate, human-readable, docstring for it.
    [10]

    The `simulate_data` function is used to generate simulated data based on a seed DataFrame. 

    Here's a brief explanation of the function:

    - `seed_df`: The seed DataFrame contains the structure of the data to be simulated. Each row represents a representative point, and each column represents a feature.
    - `n_points`: The number of simulated points to generate for each representative point in the seed DataFrame.
    - `col_specs`: A dictionary that specifies the distribution of the data for each column. If not provided, an error will be raised.
    - `random_state`: An integer that specifies the random seed for reproducibility. If not provided, the results will not be reproducible.

    The function iterates over each representative point in the seed DataFrame and generates `n_points` simulated points for each representative. For each simulated point, it applies column-specific specifications (if provided) to generate the values for each feature. The supported distributions are 'normal' and 'uniform'. If a column has no specifications in `col_specs`, an error will be raised.

    The function returns a DataFrame with the simulated data, where each row represents a simulated point and each column represents a feature.


4) Write a demo file, called "demo1_cm.py", that demonstrate
    the use of the three functions of the package. The type of
    demonstration is up to you, but it should be clear and 
    informative. 
    [10]
    
   Overall, this code allows the user to define the structure of a DataFrame by specifying the column names, repetitions, distribution, and variance. It provides a simple interface for generating simulated data based on the defined structure and exporting it to a CSV file. This code prompts the user to define the structure of a DataFrame and simulate data based on the defined structure. It then exports the simulated data to a CSV file in the data directory.

    Here's a step-by-step breakdown of what the code does:

    1. It prints a description of what the code does.
    2. It imports a module called cluster_maker using the import statement.
    3. It initializes an empty list called column_specs to store the specifications of each column in the DataFrame.
    4. It prompts the user to enter the number of columns they want in the DataFrame.
    5. It enters a loop that iterates num_columns times.
    6. Inside the loop, it prompts the user to enter the name for each column and the repetitions for that column (comma-separated).
    7. It converts the repetitions from strings to floats and stores them in a list called column_reps.
    8. It appends a dictionary containing the column name and repetitions to the column_specs list.
    9. It initializes an empty dictionary called col_specs to store the column specifications for the simulation.
    10. It enters a loop that iterates over each column_spec in column_specs.
    11. Inside the loop, it prompts the user to enter the distribution for the current column (either 'normal' or 'uniform').
    12. It validates the user's input, ensuring that it is either 'normal' or 'uniform'.
    13. It prompts the user to enter the variance for the current column.
    14. It stores the column distribution and variance in the col_specs dictionary, using the column name as the key.
    15. The code execution ends here.


5) Add to "data_exporter.py" a function called export_formatted()
    that exports the data created to a formatted text file. The
    formatting should make the file human-readable and informative.
    [20]
  
   The `export_formatted` function is used to export a DataFrame to a formatted text file. 

    Here's a brief explanation of the function:

    - `data`: The input DataFrame that needs to be exported.
    - `filename`: The name of the output text file.

    The function also includes a nested function called `missing_values`, which calculates the percentage of missing values and zeros in each column of the input DataFrame.

    The `export_formatted` function first calls the `missing_values` function to generate a DataFrame containing information about the columns, such as the number of unique values, the percentage of missing values, and the percentage of zeros.

    Then, it opens the output text file and writes the data information, including the number of rows and columns, followed by the information from the `missing_values` DataFrame. Finally, it writes the actual data from the input DataFrame.

    If the export is successful, it prints a message indicating the successful export. If there is an error, it prints an error message with the specific exception encountered.



6) Add a function, called non-globular_cluster(), to 
    dataframe_builder.py, that tries to simulate non-globular
    clusters. Similarly to simulate_data(), this function should
    take the seed data structure (the dataframe created by 
    define_dataframe_structure()) and the number of points to
    simulate, but also whatever parameters you think are necessary.
    [30]

    The `non_globular_cluster` function is used to simulate non-globular clusters based on a seed DataFrame. Here's a brief explanation of the function:

    - `seed_df`: The seed DataFrame contains the structure of the data to be simulated. Each row represents a representative point, and each column represents a feature.
    - `n_points`: The number of simulated points to generate for each representative point in the seed DataFrame.
    - `col_specs`: A dictionary that specifies the distribution of the data for each column. If not provided, an error will be raised.
    - `random_state`: An integer that specifies the random seed for reproducibility. If not provided, the results will not be reproducible.
    - `cluster_params`: A dictionary that contains the parameters for simulating non-globular clusters.

    The function first checks if the `cluster_params` dictionary is provided. If not, it raises a `ValueError` indicating that cluster parameters are required.

    Then, it initializes an empty list called `simulated_data` to store the simulated points.

    The function iterates over each representative point in the seed DataFrame and generates `n_points` simulated points for each representative. For each simulated point, it applies column-specific specifications (if provided) to generate the values for each feature. The supported distributions are 'normal' and 'uniform'. If a column has no specifications in `col_specs`, an error will be raised.

    After generating the simulated point, the function applies a non-globular transformation to the specified columns. The transformation is specified by the `cluster_params` dictionary, which contains the column names as keys and the transformation functions as values. The supported transformation functions are 'exp', 'log', 'sqrt', and 'linear'.

    Finally, the function appends the simulated point to the `simulated_data` list.

    The function returns a DataFrame with the simulated non-globular clusters, where each row represents a simulated point and each column represents a feature.



