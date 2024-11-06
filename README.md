
Context是应用中对象的上下文，其提供了应用的一些基础信息，例如resourceManager（资源管理）、applicationInfo（当前应用信息）、dir（应用文件路径）、area（文件分区）等，以及应用的一些基本方法，例如createBundleContext()、getApplicationContext()等。UIAbility组件和各种ExtensionAbility派生类组件都有各自不同的Context类。分别有基类Context、ApplicationContext、AbilityStageContext、UIAbilityContext、ExtensionContext、ServiceExtensionContext等Context。


## Context继承关系


![img1](https://alliance-communityfile-drcn.dbankcdn.com/FileServer/getFile/cmtyPub/011/111/111/0000000000011111111.20241105123302.16130934653031467270079942435561:50001231000000:2800:19F1AEA212128F42D9B14864FF03FBFFC6B9DB82A14499540295DF17DDC00D2F.png)


## 获取UIAbilityContext


每个UIAbility中都包含了一个Context属性，提供操作应用组件、获取应用组件的配置信息等能力



```
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let uiAbilityContext = this.context;
    //...
  }
}

```

## 获取特定场景ExtensionContext


以ServiceExtensionContext为例，表示后台服务的上下文环境，继承自ExtensionContext，提供后台服务相关的接口能力。



```
import { ServiceExtensionAbility, Want } from '@kit.AbilityKit';

export default class ServiceExtAbility extends ServiceExtensionAbility {
  onCreate(want: Want) {
    let serviceExtensionContext = this.context;
    //...
  }
}

```

## 获取AbilityStageContext


Module级别的Context，和基类Context相比，额外提供HapModuleInfo、Configuration等信息



```
import { AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate(): void {
    let abilityStageContext = this.context;
    //...
  }
}

```

## 获取ApplicationContext


应用级别的Context。ApplicationContext在基类Context的基础上提供了订阅应用内应用组件的生命周期的变化、订阅系统内存变化和订阅应用内系统环境的变化的能力，在UIAbility、ExtensionAbility、AbilityStage中均可以获取。



```
import { UIAbility, AbilityConstant, Want } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    let applicationContext = this.context.getApplicationContext();
    //...
  }
}

```

 本博客参考[悠兔机场](https://xinnongbo.com)。转载请注明出处！
