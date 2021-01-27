# Recommendation Systems

## SVD

Latent factors behind the user data -> hidden factors that affect an user's behaviors

**X = USV'**

(N_user, N_movie) = (N_user, N_latent) x (N_latent, N_latent) x (N_latent, N_movie)

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

## FunkSVD

