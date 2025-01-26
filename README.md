# quake.world-data
Misc data used by Quake.World.

```sh
# mice.json (https://www.eloshapes.com/mouse/database)
jq -c '[.[] | {name: (.brand_name + " " + .model),wireless,dpi,polling_rate}] | sort_by(.name) | unique_by(.name)' source.json > mice.json
```
