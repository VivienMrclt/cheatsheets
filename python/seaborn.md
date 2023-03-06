# Seaborn

[Documentation](https://seaborn.pydata.org/api.html)

Import the module
```python
import seaborn as sns
```

## Create a diagram

- sns.scatterplot(data=prets, x='revenu', y='taux', hue='type')
- sns.barplot(data=prets, x='ville', y='remboursement', ci=None, estimator=sum)
- sns.lineplot
- sns.boxplot
- sns.histplot
- sns.kdeplot
- sns.pairplot

## Style

- sns.set\_palette('pastel')
https://seaborn.pydata.org/tutorial/color\_palettes.html?highlight=color

- sns.set\_theme(style='whitegrid', palette='pastel')

