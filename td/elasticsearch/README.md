# Workflow: td example (Result Output to Elasticsearch)

This example workflow exports TD job results into Elasticsearch, using [Treasure Data's Writing Job Results into Elasticsearch](https://docs.treasuredata.com/articles/result-into-elasticsearch) with [td](http://docs.digdag.io/operators/td.html) operator.

# Prerequisites

In order to register your credential in TreasureData, please create connection setting on [Connector UI](https://console.treasuredata.com/app/connections).

![](https://t.gyazo.com/teams/treasure-data/021eaa8477c5d633e9e563214214af1d.png)

![](https://t.gyazo.com/teams/treasure-data/3e597e5d4bbd7e6753b5e44ae16b0363.png)

The connection name is used in the dig file.

# How to Run

First, please upload your workflow project by `td wf push` command.

    # Upload
    $ td wf push sample_project

If you want to mask setting, please set it by `td wf secrets` command. For more details, please see [digdag documentation](http://docs.digdag.io/command_reference.html#secrets)

    # Set Secrets
    $ td wf secrets --project sample_project --set key=value

    # Set Secrets on your local for testing
    $ td wf secrets --local --set key=value

Now you can use these secrets by `${secret:}` syntax in the dig file.

You can trigger the session manually.

    # Run
    $ td wf start sample_project td_elasticsearch --session now

## Local mode

    # Run
    $ td wf run td_elasticsearch.dig

# Supplemental

Available parameters for `result_settings` are here.

- mode: (string(insert|replace), default insert)
- index: (string, required)
- index_type: (string, required)
- id_field: (string, default null)
- bulk_actions: (int, default 1000)
- bulk_size: (long, default 5242880)
- concurrent_requests: (int, default 5)

For more details, please see [Treasure Data documentation](https://docs.treasuredata.com/articles/result-into-elasticsearch).

# Next Step

If you have any questions, please contact support@treasure-data.com.
