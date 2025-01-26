# quake.world-data
Misc data used by Quake.World.

```sh
# mice.json (https://www.eloshapes.com/mouse/database)
jq -c '[.[] | {name: (.brand_name + " " + .model),wireless,dpi,polling_rate}] | sort_by(.name) | unique_by(.name)' source.json > mice.json

# mousepads.json (https://prosettings.net/gear/lists/mousepads/)
curl --silent https://prosettings.net/gear/lists/mousepads/ | htmlq --text '#equipment-list-table tbody td:nth-child(2) a' | sed 's/^ *//g' | sort -V | jq -R -s 'split("\n") | map(select(length > 0))' > mousepads.json
```
