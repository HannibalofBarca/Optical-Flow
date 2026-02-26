# Optical-Flow
This project provides a manual implementation of the Lucas-Kanade Optical Flow algorithm.

### Notes:

1. The algorithm begins by identifying corner features in the previous frame using an implementation of the Shi-Tomasi corner detector
2. For the whole image, it calculates the spatial gradients ($I_x$ and $I_y$) using a 3x3 Sobel operator, as well as the temporal gradient ($I_t$) by finding the pixel intensity difference between the current frame and the previous frame.
3. For each detected feature, the script extracts a local window (e.g., $16 \times 16$ pixels). It flattens the gradients within this window to build the matrices for the Lucas-Kanade system:
   $$A = \begin{bmatrix} I_x & I_y \end{bmatrix}$$
   $$\mathbf{b} = -I_t$$
   
4. It then solves the overdetermined linear system using least squares to find the displacement vector $\begin{bmatrix} u \\ v \end{bmatrix}$ for that specific feature:
   $$A^T A \begin{bmatrix} u \\ v \end{bmatrix} = A^T \mathbf{b}$$
   The code checks the eigenvalues of $A^T A$ to ensure the matrix is invertible
   


https://github.com/user-attachments/assets/ee36145f-bb7c-4e2b-846a-1ceb9467cb29

