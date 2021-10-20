The main goal of the reporting subsystem is to be a graphical interface to view collected data on their game.

## Overview of the Reporting Subsystem

## Key Features

## APIs

### GET

### /count_dat_files

url parameters:

```json
{}
```

This endpoint gets the total number of .dat files. This will inform the frontend of how many different files we have to display to the user. This will also inform the frontend of the range of the dat file id - which is used to refer to specific files. For example, a dat file id of 0 means generate heatmap for the first dat file.

### /by_reward/\<type>/\<percentage>/\<dat_id>

url parameters:

```json
{
  "type": "string",
  "percentage": "float",
  "dat_id": "int"
}
```

This endpoint returns a heatmap that filters episodes by their reward for a given dat file. Parameters are type ("top"/"bottom"), percentage (a float between 0 and 1), dat file id.

### /by_episode_length/\<type>/\<percentage>/\<dat_id>

url parameters:

```json
{
  "type": "string",
  "percentage": "float",
  "dat_id": "int"
}
```

This endpoint returns a heatmap that filters episodes by their length for a given dat file. Parameters are type ("top"/"bottom"), percentage (a float between 0 and 1), dat file id.

### /naive/<dat_id>

url parameters:

```json
{
  "dat_id": "int"
}
```

This endpoint returns the heatmap for a given dat file id. Parameters is a dat file id.

### /last_position/<dat_id>

url parameters:

```json
{
  "dat_id": "int"
}
```

This endpoint returns a heatmap showing the last position of every episode in a dat file. Parameters is a dat file id.
