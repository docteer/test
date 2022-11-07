from requests import get

port = 8080
base_url = f'http://localhost:{port}'


def main():
    locations = get(f'{base_url}/sites/location')
    loc_data = locations.json()
    for site in loc_data:
        print(f"Site with id {site['site_id']} has location with lat {site['coords'][0]} and lng {site['coords'][1]}")

    locations = get(f'{base_url}/sites/data')
    data = locations.json()
    for site in data:
        print(site)

    locations = get(f'{base_url}/maintenance')
    mt_data = locations.json()
    for site in mt_data:
        print(site)

    # 2xx = alles gut
    # 3xx = redirect
    # 4xx = client error
    # 5xx = server error


if __name__ == "__main__":
    main()
