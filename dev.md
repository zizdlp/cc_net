# dev

```shell
python -m cc_net --config reproduce --dump 2019-09 --cache_dir /tmp/ccnet_data
python -m cc_net --config reproduce --dump 2019-09 --cache_dir /tmp/ccnet_data --num_shards 100
python -m cc_net --dump 2019-09 --cache_dir /tmp/ccnet_data --num_shards 100
```

```shell
python -m cc_net --dump 2019-09 --cache_dir /tmp/ccnet_data --num_shards 100 --hash_in_mem 5

pipeline=['dedup', 'lid', 'keep_lang', 'sp', 'lm', 'pp_bucket', 'drop', 'split_by_lang']
1. 生成hash
2. 去重，这里内存要求高，改为--hash_in_mem 5
3. Not found: "data/lm_sp/de.sp.model": No such file or directory Error #2
---> `make dl_all_lms` 下载所有语言的模型
```

```shell
python -m cc_net --dump 2019-09 --cache_dir /app/cache_data --num_shards 1 --hash_in_mem 1 --num_segments_per_shard 40

pipeline=['dedup', 'lid', 'keep_lang', 'sp', 'lm', 'pp_bucket', 'drop', 'split_by_lang']
1. 生成hash
2. 去重，这里内存要求高，改为--hash_in_mem 5
3. Not found: "data/lm_sp/de.sp.model": No such file or directory Error #2
---> `make dl_all_lms` 下载所有语言的模型
```

## server

```shell
scp  -r /tmp/ccnet_data root@69.230.245.151:/tmp/ccnet_data
```

```shell
zcat data/mined/2019-09/eo_all_0000.json.gz | head -1 | jq .
```

python -m cc_net --dump 2019-18 --cache_dir /root/wxl_folder/cached_data --num_shards 10 --hash_in_mem 10


python -m cc_net --dump 2019-18 --cache_dir /metadata0/wxl_data/cached_data/commoncrawl_data/ --output_dir /metadata0/wxl_data/data  --num_shards 1 --lm_dir /metadata0/wxl_data/lm_sp