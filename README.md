# erpnext_portable
Portable ERPNext

Works both on macOS and Linux.

## install  Miniconda3

``` bash
sudo apt install cron
wget https://repo.anaconda.com/miniconda/Miniconda3-py39_4.12.0-Linux-x86_64.sh -O ~/miniconda.sh
bash ~/miniconda.sh -b -p miniconda
```
## create virtual enviroment for erpnext 

```bash
source miniconda/bin/activate
conda env list

conda create -n erpnext -y -c conda-forge python=3.10 nodejs=16 yarn postgresql \
redis-server nginx wkhtmltopdf conda conda-pack git
```

## install frappe-bench

```
conda activate erpnext
pip install frappe-bench
```
## init and start Postgres

- username postgres
- password no
- directory pgdata
- port 5432

```
# init pg
initdb -D  pgdata  -U postgres -E UTF-8 --no-locale
# start pg
pg_ctl -D pgdata -l logfile start -o'-p 5432'
```

## Create the frappe-bench directory

```bash
bench init erpnext
```

## create your first website

```
bench new-site library.test --db-type postgres
# set library.test as default website
echo library.test>sites/currentsite.txt
```

## install ERPNext app

```
bench get-app payments
bench get-app erpnext
bench install-app erpnext
```

## start ERPNext
```bash
bench start
```

## more tutorials

https://frappeframework.com/docs/v14/user/en/introduction