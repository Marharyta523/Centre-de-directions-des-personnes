from tabulate import tabulate
import random
num_points = 100_000
points = [(random.randit(0 , 1000), random.randit(0 , 1000)) for _ in range(num_points)]
points_sorted = sorted(points, key=lambda p: p [0] * p[1])
n = len(points_sorted)
k = int(n * 0.10)
start_points = points_sorted[:k]
end_points = points_sorted[-k:]
points = [(x1 , y1), (x2 , y2), ...]
points_with_product = [(x , y , x*y) for x, y in points]
points_sorted = sorted(points_with_product, key=lambda p: p[2], reverse=False)
n = len(points_sorted)
k = int(n * 0.10)
top_candidats = points_sorted[-k:]
points_coords = [(x , y) for x, y, *rest in top_candidates]
import math
max_dist = 0
point_pair = None
for a in range(len(points_coords)):
	for b in range(a+1 , len(points_coords)):
		d = math.sqrt((points_coords[b][0] - points_coords[a][0])**2 + 
			          (points_coords[b][1] - points_coords[a][1])**2)**0.5
		if d > max_dist:
			max_dist = d 
			point_pair = (points_coords [a], points_coords[b])
segment = point_pair
x1 , y1 = segment[0]
x2 , y2 = segment[1]
dx = x2 - x1
dy = y2 - y1
for px , py in points_coords:
	t= ((px - x1)* dx + (py - y1) * dy) / (dx*dx + dy*dy)
	t_clamped = max(0 , min(1 , t))
	proj_x = x1 + t_clamed * dx 
	proj_y = y1 + t_clamed * dy
	projection = (proj_x , proj_y)
projections = [(px1 , py1), (px2, py2), ...]
n = len(projections)
sum_x = sum(p[0] for p in projections)
sum_y = sum(p[1] for p in projections)
center_x = sum_x / n 
center_y = sum_y / n 
center = (center_x , center_y)
