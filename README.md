import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("salario_profissionais_dados.csv")

df.head(5)

df.shape

df.info()

df.isnull().sum()

df[['job_title', 'experience_level', 'company_size']].value_counts(normalize=True).head(10)

df.describe()

sns.histplot(df['salary_in_usd'], kde=True)
plt.title('Distribuição de Salários em USD')
plt.show()

media_experiencia = df.groupby('experience_level')['salary_in_usd'].mean().sort_values()
print(media_experiencia)

sns.boxplot(x='experience_level', y='salary_in_usd', data=df)
plt.title('Salário por Nível de Experiência')
plt.show()

df.groupby('employee_residence')['salary_in_usd'].mean().sort_values(ascending=False)

df[['salary_in_usd', 'work_year', 'years_of_experience']].corr()
