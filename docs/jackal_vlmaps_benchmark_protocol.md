# Jackal VLMaps Benchmark Protocol

## Benchmark maps

The final benchmark uses six canonical VLMaps:

- I0
- I25
- I50
- O20
- O50
- O80

Each map contains the complete benchmark scene with all 10 target
objects.

A single VLMap is reused for all object queries and all four navigation
starting positions belonging to the same condition.

Therefore:

6 conditions × 10 objects × 4 starts = 240 navigation episodes.

## Illumination conditions

I0, I25 and I50 contain the same geometry and the same 10 objects.

Only the illumination condition changes.

## Occlusion conditions

For O20, all 10 benchmark objects are simultaneously subject to the
nominal 20% visual occlusion.

For O50, all 10 objects use 50% occlusion.

For O80, all 10 objects use 80% occlusion.

Occluders are visual-only and must not modify the physical navigation
environment.

## Mapping acquisition

All six conditions must use the same predefined camera/robot poses.

Manual independent mapping trajectories must not be used.

At every predefined pose the acquisition system records:

- RGB image
- depth image
- camera pose
- timestamp

The same ordered pose list is replayed for every condition.

## Mapping quality

Before building a VLMap, each dataset must satisfy:

- identical RGB/depth/pose counts;
- identical camera intrinsics;
- identical acquisition poses between conditions;
- valid depth measurements;
- all 10 objects present;
- multiple useful observations of every target;
- adequate spatial coverage of the warehouse.

## Frame selection

Final benchmark acquisition will use deliberately selected mapping
viewpoints.

`skip_frame` will be frozen before the benchmark and kept identical
for every condition.

If only selected keyframes are stored, `skip_frame=1` should be used.

## Pilot map

`warehouse_jackal_01` is considered an integration pilot only.

It must not be used for final benchmark results because:

- it predates the final 10-object benchmark scene;
- its camera coverage is incomplete;
- the pilot was generated with `skip_frame=20`.

