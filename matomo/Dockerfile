FROM docker.io/matomo:5.1.1

python /var/www/html/misc/log-analytics/import_logs.py --url=http://localhost  --login=user --password=matomo --idsite=2 --recorders=4 /apache/access_log.log

./console core:archive --force-all-websites --url='http://localhost'