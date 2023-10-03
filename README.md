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
gdp_china=gapminder['China']
print(gdp_china)

import pytest
from python_repos_tested_yu import get_repos_info, get_response_dict, get_repo_dicts

def test_response_status_code():
    "test a response that has a successful status code"
    r = get_repos_info()
    assert r.status_code == 200

def test_response_dict():
    """Verify an appropriate number of repositories are represented,
    and the results are complete.
    """
    r = get_repos_info()
    response_dict = get_response_dict(r)

    total_count = response_dict['total_count']
    complete_results = not response_dict['incomplete_results']

    assert total_count > 240
    assert complete_results

def test_repo_dicts():
    "verify the results in repo_dict are correct"
    r = get_repos_info()
    response_dict = get_response_dict(r)
    repo_dicts = get_repo_dicts(response_dict)

    assert len(repo_dicts) == 30
    
    # Check that all repos returned have over 10k stars.
    for repo_dict in repo_dicts:
        assert repo_dict['stargazers_count'] > 10_000




