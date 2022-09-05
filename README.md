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


# 日志格式约束

- 参数小写 （zap.String("commit","v1.0.0"")）
- Info,Error (第一个单词大写)

```shell
	m.log.Info("Welcome to InfluxDB",
		zap.String("version", info.Version),
		zap.String("commit", info.Commit),
		zap.String("build_date", info.Date),
	)
```

- 示例

```shell
m.log.Error("Failed creating new secret store", zap.Error(err))
```

- 示例 程序关闭

```shell
log.Info("Stopping")
```

- 示例

```shell
log.Error("Missing metadata for bucket.", zap.String("bucket", bucket.Name), zap.Stringer("bucket_id", bucket.ID))
```

- 示例

```shell
s.log.Info("Resources opened", zap.String("path", s.path))
```

- Debug 和 Warn使用

```shell
	indexPath := filepath.Join(dataDir, "index")
	log.Debug("Checking index path", zap.String("path", indexPath))
	if _, err := os.Stat(indexPath); !os.IsNotExist(err) {
		log.Warn("tsi1 index already exists, skipping", zap.String("path", indexPath))
		return nil
	}
```