
https://github.com/Kaggle/kaggle-api

### Basic Examples

```bash
export KGL_COMP=tweet-sentiment-extraction

kaggle config view
kaggle config set -n competition -v $KGL_COMP
kaggle config view
```

Check competition kernels
```bash
kaggle k list --competition $KGL_COMP --sort-by scoreDescending

```

Check competition leaderboard
```bash
kaggle competitions leaderboard $KGL_COMP -s

```

Download all data of a competition
```bash
kaggle competitions download $KGL_COMP -f test.csv.7z
```

Make a submission on the current competition
```bash
kaggle competitions submit $KGL_COMP -f sample_submission.csv.7z -m "My submission message"
```

List my submissions on the current competition
```bash
kaggle c submissions $KGL_COMP
```
....
====

ToDo:

- [ ] Find a way to get score of a kernel
- [ ] Perform kernel Init & Run
- [ ] Prepare proper pipeline for testing & monitoring
