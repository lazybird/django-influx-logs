# Django Influx Logs

Put your application logs into InfluxDB

### Install


`pip install django-influx-logs`


### Settings

```
INFLUX_LOGS_ENABLE = True
INFLUX_LOGS_HOST = "localhost"
INFLUX_LOGS_PORT = 8086
INFLUX_LOGS_USERNAME = "my_user"
INFLUX_LOGS_PASSWORD = "mu_psw"
INFLUX_LOGS_DATABASE = "my_db"
```

### Usage example

```
class SomeDownloadView(View):

    def log_download_action(self, filename):
        tags = {"env_name": "staging"}
        log_action(
            actor=self.request.user.email,
            verb="downloaded",
            action_object=filename,
            tags=tags,
        )

    def get(self):
        # At some point here, we want to log the user's action
        self.log_download_action(filename="my-file.txt")
```
