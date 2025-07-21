# Python_Basic
Data Visualization Python


# DailyStudy

![GitHub repo size](https://img.shields.io/github/repo-size/iuricode/README-template?style=for-the-badge)
![GitHub language count](https://img.shields.io/github/languages/count/iuricode/README-template?style=for-the-badge)
![GitHub forks](https://img.shields.io/github/forks/iuricode/README-template?style=for-the-badge)
![Bitbucket open issues](https://img.shields.io/bitbucket/issues/iuricode/README-template?style=for-the-badge)
![Bitbucket open pull requests](https://img.shields.io/bitbucket/pr-raw/iuricode/README-template?style=for-the-badge)

### Day 1: Data loading:


- Read CSV FILE
  ```
  df = pd.read_csv("/content/imigrantes_canada.csv")
  df.head()
  ```
-Change the index of the project
```
df.set_index("País", inplace=True)
df.head()
```
- Counting in each country
```
per year
anos = list(map(str, range(1980, 2014)))
brasil = df.loc['Brasil', anos]
brasil

brasil_dict = {'Ano': brasil.index.tolist(), 'Imigrantes': brasil.values.tolist()}
dados_brasil = pd.DataFrame(brasil_dict)
dados_brasil.head()
```

```First graphic
plt.figure(figsize=(8,4))
plt.plot(dados_brasil['Ano'], dados_brasil['Imigrantes'])
plt.xticks(['1980', '1985', '1990', '1995', '2000', '2005', '2010','2014'])
plt.yticks([500, 1000, 1500, 2000, 2500, 3000])
plt.xlabel('Ano')
plt.ylabel('Número de imigrantes')
plt.show()

```

### Day 2 Boxplot

```Compare two countries
df_comparacao = df.loc[['Brasil', 'Argentina', 'Chile'], anos]
df_comparacao = df_comparacao.T
df_comparacao.head(
```

``` Create graphic
fig, ax = plt.subplots(figsize=(8,4))
ax.plot(dados_brasil['Ano'], dados_brasil['Imigrantes'])
ax.set_title('Imigração do Brasil para o Canadá\n1980 a 2013')
ax.set_xlabel('Ano')
ax.set_ylabel('Número de imigrantes')
ax.xaxis.set_major_locator(plt.MultipleLocator(5))
plt.show()
```
```boxplot
fig, axs = plt.subplots(1, 2, figsize=(15, 5))

axs[0].plot(dados_brasil['Ano'], dados_brasil['Imigrantes'])
axs[0].set_title('Imigração do Brasil para o Canadá\n1980 a 2013')
axs[0].set_xlabel('Ano')
axs[0].set_ylabel('Número de imigrantes')
axs[0].xaxis.set_major_locator(plt.MultipleLocator(5))

axs[1].boxplot(dados_brasil['Imigrantes'])
axs[1].set_title('Boxplot da imigração do Brasil para o Canadá\n1980 a 2013')
axs[1].set_xlabel('Brasil')
axs[1].set_ylabel('Número de imigrantes')


plt.show()
```

``` Subplots with 4 countries
fig, axs = plt.subplots(2,2, figsize=(10,6))
fig.subplots_adjust(hspace=0.5, wspace=0.3)
fig.suptitle('Imigração dos quatro maiores países da América do Sul para o Canadá de 1980 a 2013')


axs[0,0].plot(df.loc['Brasil', anos])
axs[0,0].set_title('Brasil')

axs[0,1].plot(df.loc['Colômbia', anos])
axs[0,1].set_title('Colômbia')

axs[1,0].plot(df.loc['Argentina', anos])
axs[1,0].set_title('Argentina')

axs[1,1].plot(df.loc['Peru', anos])
axs[1,1].set_title('Peru')

for ax in axs.flat:
  ax.xaxis.set_major_locator(plt.MultipleLocator(5))

for ax in axs.flat:
  ax.set_xlabel('Ano')
  ax.set_ylabel('Número de imigrantes')


ymin = 0
ymax = 7000

for ax in axs.ravel():
  ax.set_ylim(ymin, ymax)

plt.show()
```
### Day 3 Filter by Region

```
america_sul = df.query('Região == "América do Sul"')
america_sul
```

```
Order by value
america_sul_ordenado = america_sul.sort_values('Total', ascending=False)
or
top_10 = df.sort_values('Total',ascending=False).head(10)
top_10

```
```
##Focus in one specific country##

cores = []
for pais in america_sul_ordenado.index:
    if pais == 'Brasil':
        cores.append('red')
    else:
        cores.append('silver')

fig, ax = plt.subplots(figsize=(12, 5))
ax.barh(america_sul_ordenado.index, america_sul_ordenado['Total'], color=cores)
ax.set_title('América do Sul: Brasil foi o quarto país com mais imigrantes\npara o Canadá no período de 1980 a 2013', loc='left', fontsize=16)
ax.set_xlabel('Número de imigrantes', fontsize=14)
ax.set_ylabel('')
ax.set_xlabel('Número de imigrantes', fontsize=14)
ax.yaxis.set_tick_params(labelsize=12)
ax.xaxis.set_tick_params(labelsize=12)

for i, v in enumerate(america_sul_ordenado['Total']):
    ax.text(v + 20, i, str(v), color='black', fontsize=10, ha='left', va='center')

ax.set_frame_on(False)
ax.get_xaxis().set_visible(False)
ax.tick_params(axis='both',which='both',length=0)

plt.show()
```









### Adjustments and improvements.

The project is still under development, and the upcoming updates will focus on the following tasks:

- [x] Advanced courses about Phyton

The following tools were used in the construction of the project:

- [Python](<https://www.python.org/doc//>)



## 🤝 Creator

<table>
  <tr>
    <td align="center">
      <a href="#" title="Thales Farias">
        <img src="grecia.jpg" width="100" alt="Foto do Thales Farias no GitHub"/><br>
        <sub>
          <b><a href="https://www.linkedin.com/in/thalesfreirefarias/" target="_blank">Thales Farias</b>
        </sub>
      </a>
    </td>
  </tr>
</table>
