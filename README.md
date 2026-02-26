# Optical-Flow
This project provides a manual implementation of the Lucas-Kanade Optical Flow algorithm.

### Notes:

1. The algorithm begins by identifying corner features in the previous frame using an implementation of the Shi-Tomasi corner detector
2. For the whole image, it calculates the spatial gradients (I_x and I_y) using a 3x3 Sobel operator, as well as the temporal gradient I_t by finding the pixel intensity difference between the current frame and the previous frame.
3. For each detected feature, the script extracts a local window (e.g., $16 \times 16$ pixels). It flattens the gradients within this window to build the matrices for the Lucas-Kanade system:
   * Matrix A = [Ix, Iy]
   * Vector b = -It
   
4. It then solves the overdetermined linear system using least squares to find the displacement vector [u, v]^T for that specific feature:
   * (A^T * A) * [u, v]^T = A^T * b
   The code checks the eigenvalues of (A^T * A) to ensure the matrix is invertible
   


https://github.com/user-attachments/assets/62b472f8-bdce-42b2-9a51-65d688fcefb0

