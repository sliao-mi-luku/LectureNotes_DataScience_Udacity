# Recommendation Systems

## SVD

Latent factors behind the user data -> hidden factors that affect an user's behaviors

**X = USV'**

(N_user, N_movie) = (N_user, N_latent) x (N_latent, N_latent) x (N_latent, N_movie)

The **square** of the diagonal element of S gives the variability proportion it captures in the original matrix


Better to check the dimension returned by `np.linalg.svd`

```python3
u, s, vt = np.linalg.svd(user_movie_matrix)

# n_max = max(n_user, n_movie)
# n_min = min(n_user, n_movie)
# u.shape = (n_max, n_max)
# s.shape = (n_min, )
# vt.shape = (n_min, n_min)

S = np.diag(s)
```

Any NaN in the original matrix will raise `LinAlgError` when running np.linalg.svm(). SVD can't work with missing values.

## FunkSVD

FunkSVD works with missing values by learning matrices **U** and **V'**.

The idea:

```
1. Inititiate matrices U and V'
2. Given a user U[i, :] and a movie V'[:, j], predict the outcome by y_pred = U[i, :] * V'[:, j] = u_i * v_j
3. Calculate the error (squared error) = (y_true - y_pred)**2 = (y_true - u_i * v_j)**2
4. Gradient descent to update all elements in U[i, :]
    U[i, :] = U[i, :] - 2*learning_rate*(y_true - U[i, :]* V'[:, j])*V'[:, j]
5. Gradient descent to update the elements in V'[:, j]
    V'[:, j] = V'[:, j] - 2*learning_rate*(y_true - U[i, :]* V'[:, j])*U[i, :]
```




