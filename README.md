# nestjs-autoconfigure

A [nestjs module](https://docs.nestjs.com/modules) for autoconfiguring other nestjs modules.
This idea is borrowed from [spring-boot-autoconfigure](https://docs.spring.io/spring-boot/docs/current/reference/html/using-spring-boot.html#using-boot-auto-configuration).

| This project is still experimental. |
|-------------------------------------|

## Idea

Given a generic nestjs `AppModule`:

```ts
import { Module } from '@nestjs/common';
import { AutoConfigurationModule } from '@devcsrj/nestjs-autoconfigure';

@Module({
  imports: [AutoConfigurationModule],
})
export class AppModule {}
```

It will automatically populate the nestjs application context with providers according to
various conditions such as:
 - Existence of a property (`e.g.: database.url`)
 - Existence of a dependency (`e.g.: @nestjs/typeorm, typeorm`)
 - Lack of a provider (`e.g.: DataSource`)
