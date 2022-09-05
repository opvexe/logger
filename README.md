# 示例

- error

```shell
	s.Logger.
				WithField("component", "apps").
				WithField("name", name).
				Error("Invalid Layout: ", err)
```

- info 

```shell
		logger.
			WithField("component", "server").
			WithField("realm", s.BasicAuthRealm).
			WithField("htpasswd", s.BasicAuthHtpasswd).
			Info("Configuring HTTP basic authentication")
```

- log 

```shell
	logger := clog.New(clog.ParseLevel(s.LogLevel))
	customLinks, err := NewCustomLinks(s.CustomLinks)
	if err != nil {
		logger.
			WithField("component", "server").
			WithField("CustomLink", "invalid").
			Error(err)
		return
	}
```