# lab-3-server
Creating a spring cloud server to provide config file

This project look up for a git repository to get a config file and serve it.

After start the application you should call:
```
http://localhost:<port in properties>/<application name in properties>/<spring activated profile>
```

In this case:
```
http://localhost:8001/lab-3-client/default/
```
You should see:
```
{
  name: "lab-3-client",
  profiles: [
    "default"
  ],
  label: null,
  version: "8820c4dd1322aab5688b0737f0afc3e064da0f67",
  state: null,
  propertySources: [
    {
      name: "https://github.com/diegocmsantos/ConfigData/lab-3-client.yml",
      source: {
        lucky-word: "tobias"
      }
    }
  ]
}
```

## File structure
The file in git repository should respect the following rules:
<application name>-<activated profile>.[yml | properties]

## Precedence
In the current example the server would respect the following precedence:
lucky-word-default.yml (first precedence)
lucky-word.yml (if exists, second precedence)
another-app.yml (will be ignored, it has another app name)
lucky-word.properties (if exists, second precedence)
