from jira import JIRA

jira_url = "https://name.jira.instance.com/"
jira_api_token = "your_api_tocken"

target_version = "6.15.0"
affectedVersion = "6.15.0"
data = {
    'Release Pending Backlog': f'project = Satellite AND type = Bug AND "Target Version" = {target_version}',
    'Release Pending Blockers': f'project = Satellite AND type = Bug AND component != Documentation AND ("Target Version" = {target_version} OR affectedVersion = {affectedVersion})',
}



def fetch_jira_count():
    # Dict which have name and it's count
    data_set = {}

    # Creating Jira client with token authentication
    jira = JIRA(server=jira_url, token_auth=jira_api_token)

    # Fetching the count based on the provided JQL filter
    for name, filter in data.items():
        count = len(jira.search_issues(filter))
        data_set[name] = count
    return data_set


print(fetch_jira_count())
