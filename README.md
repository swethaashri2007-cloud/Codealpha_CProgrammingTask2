# Matrix Operations Program
# Task: Implement Matrix Addition, Matrix Multiplication, and Transpose
# Using functions and 2D arrays (lists of lists)

# ----------------------------
# Function to input a matrix
# ----------------------------
def input_matrix(rows, cols):
    matrix = []
    print(f"Enter elements for a {rows}x{cols} matrix:")
    for i in range(rows):
        row = list(map(int, input(f"Row {i+1}: ").split()))
        matrix.append(row)
    return matrix


# ----------------------------
# Function to display a matrix
# ----------------------------
def display_matrix(matrix, name="Matrix"):
    print(f"\n{name}:")
    for row in matrix:
        print(" ".join(map(str, row)))


# ----------------------------
# Function for Matrix Addition
# ----------------------------
def add_matrices(A, B):
    if len(A) != len(B) or len(A[0]) != len(B[0]):
        print("Addition not possible! Matrices must have same dimensions.")
        return None
    result = [[A[i][j] + B[i][j] for j in range(len(A[0]))] for i in range(len(A))]
    return result


# ----------------------------
# Function for Matrix Multiplication
# ----------------------------
def multiply_matrices(A, B):
    if len(A[0]) != len(B):
        print("Multiplication not possible! Columns of A must equal rows of B.")
        return None
    result = [[0 for _ in range(len(B[0]))] for _ in range(len(A))]
    for i in range(len(A)):
        for j in range(len(B[0])):
            for k in range(len(B)):
                result[i][j] += A[i][k] * B[k][j]
    return result


# ----------------------------
# Function for Transpose
# ----------------------------
def transpose_matrix(A):
    rows, cols = len(A), len(A[0])
    result = [[A[j][i] for j in range(rows)] for i in range(cols)]
    return result


# ----------------------------
# Main Program
# ----------------------------
if __name__ == "__main__":
    # Example input for demonstration
    print("Matrix Operations Program")

    # Input dimensions for matrices
    r1 = int(input("Enter number of rows for Matrix A: "))
    c1 = int(input("Enter number of columns for Matrix A: "))
    A = input_matrix(r1, c1)

    r2 = int(input("Enter number of rows for Matrix B: "))
    c2 = int(input("Enter number of columns for Matrix B: "))
    B = input_matrix(r2, c2)

    display_matrix(A, "Matrix A")
    display_matrix(B, "Matrix B")

    # Matrix Addition
    print("\n--- Matrix Addition ---")
    addition_result = add_matrices(A, B)
    if addition_result:
        display_matrix(addition_result, "A + B")

    # Matrix Multiplication
    print("\n--- Matrix Multiplication ---")
    multiplication_result = multiply_matrices(A, B)
    if multiplication_result:
        display_matrix(multiplication_result, "A x B")

    # Transpose of A and B
    print("\n--- Matrix Transpose ---")
    transpose_A = transpose_matrix(A)
    transpose_B = transpose_matrix(B)
    display_matrix(transpose_A, "Transpose of A")
    display_matrix(transpose_B, "Transpose of B")# Codealpha_CProgrammingTask2
Matrix Operations
