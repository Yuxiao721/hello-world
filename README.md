# hello-world
my first repository
import plotly.express as px
import json
gapminder = px.data.gapminder()
gapminder2007 = gapminder.query('year==2007')
fig = px.scatter(gapminder,x="gdpPercap",y="lifeExp",color='continent',
                 size='pop',size_max=60,hover_name='country',animation_frame=
                 'year',log_x=True,
                 range_x=[100,100_000],range_y=[25,90],)
fig.show()
print(gapminder2007)
continent = gapminder2007['continent']
lifexp = gapminder2007['lifeExp']
fig = px.pie(
    gapminder2007,'continent','lifeExp'
)
fig.show()
print("中国历年人均gdp")

