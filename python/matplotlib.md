# Matplotlib

Import module
```python
import matplotlib.pyplot as plt
```

## Useful Links

- [Documentation](https://matplotlib.org/3.5.0/index.html)
- [Personalisation showcase](https://nbviewer.org/urls/gist.githubusercontent.com/Jwink3101/e6b57eba3beca4b05ec146d9e38fc839/raw/f486ca3dcad44c33fc4e7ddedc1f83b82c02b492/Matplotlib_Cheatsheet)

### Graphic types

- plt.scatter(): scattered points
- plt.plot(): lines, curves
- plt.bar()

```python
plt.bar(
	height=data['remboursement'],
	x=data['ville'])
```

- plt.hist(): histograms

```python
plt.hist(data['revenu'])
```

- plt.pie(): pie diagrams

```python
plt.pie(
	x=data['remboursement'],
	labels=data['ville'],
	autopct='%.2f%%')
```

### Diagram parameters

- plt.title('Title'): fontsize, fontname, color...
- plt.xlabel, plt.ylabel
- plt.figure(figsize=(10,6))
- plt.grid(axis='y')
- plt.ylim(0, 10000)
- plt.yticks([0, 100, 200, 300])
- plt.text(x, y, 'text')
- plt.rcParams.update({'font.size': 14): update the value for all
- plt.legend(bbox\_to\_anchor=(1, 1.02))

