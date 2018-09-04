## `_bulk` API
* when inserting data using `/_bulk` api (`curl -XPOST ... @data.json`) the file must terminate with new line

## Fielddata is disabled on text fields by default
You are trying to use text fields (in your mapping) for aggregations/sorting which does not work. You can only run aggregations/sorting on keyword fields. Solution: [Use Multi-Field](https://github.com/hovermind/ELK_stack/blob/master/multi-field.md)

Possible causes:
* Did not use mapping while creating index and therefore ES used dynamic mapping (during `_bulk` insertion) & ES used type `text` for `keyword` field - now you are trying to execute aggregation queries on that field (fied type should be `keyword` but dynamic mapping used `text`)
```
{
    "error": {
        "root_cause": [
            {
                "type": "illegal_argument_exception",
                "reason": "Fielddata is disabled on text fields by default. Set fielddata=true on [post_title.sortable] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory."
            }
        ],
        "type": "search_phase_execution_exception",
        "reason": "all shards failed",
        "phase": "query",
        "grouped": true,
        "failed_shards": [
            {
                "shard": 0,
                "index": "my-index"
                "node": "VbXshdquSwqnaeSD02K7vQ",
                "reason": {
                    "type": "illegal_argument_exception",
                    "reason": "Fielddata is disabled on text fields by default. Set fielddata=true on [post_title.sortable] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory."
                }
            }
        ],
        "caused_by": {
            "type": "illegal_argument_exception",
            "reason": "Fielddata is disabled on text fields by default. Set fielddata=true on [post_title.sortable] in order to load fielddata in memory by uninverting the inverted index. Note that this can however use significant memory."
        }
    },
    "status": 400
}
```
See: [Before enabling fielddata](https://www.elastic.co/guide/en/elasticsearch/reference/current/fielddata.html#before-enabling-fielddata)

## `_` in Mapping Type
`_` can only be used in mapping type for 'doc' i.e `_doc` (`_x` is wrong where x = anything other that 'doc')
