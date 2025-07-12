# Houdini
## Vellum
#### Tips
1. edge fracture可以用vellum constraint中的 __weld__ 创建glue
2. vellum constraint中的 __attach to geo__ 是用在两个不同geo之间的attach/ __glue__ 是相同物体
3. 解算时 __更新constraint__ 需要在solver中使用 __sop solver(constraints geometry)__
#### attributes
__@attractionweight__
vellumsovler中需要打开attraction weight
> 控制粘连块大小

__@weld__
> @weld=-1可以让weld失效

## Pyro
#### Tips
1. 爆炸/喷火只需要burn和temperature，density在solver里emit

density/(burn/flame) -> __Maximum__
> 不断add，直到maximum

temperature          -> __Pull__
> accelerate到达后再缓慢decelerate

velocity             -> __Add__
> 不断添加

divergence           -> __Add__
> divergence只会在初始状态下触发

## RBD
#### Tips
1. constraints如果放在broken的组中，就会失效
> @group_broken = 1;

## Flip
#### Tips
1. 小体积container用两个collider，一个常规 __volume collider__，另一个用 __surface collider__
2. 如果flip和collision object碰撞后在表面似乎有bounding box阻止，在volume collision中增加 __bandwith__
3. __density__ 可以控制flip上浮/下沉，制作泡沫
4. karma渲染ocean需要 __houdini ocean procedural__ 和 __houdini preview procedural__, houdini ocean procedural中viewport quality需要设置为1, houdini preview procedural需要在karama render 和ropouput之间

#### Flip 海洋流程
1. Ocean Spectrum
2. Ocean Foam
3. Flip Sim
4. Merge
5. White Water Sim
