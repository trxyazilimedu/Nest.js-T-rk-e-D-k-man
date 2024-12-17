# Nest.js Proje Yapısı ve Mimari Kılavuzu

## 1. Giriş

Nest.js, Node.js için güçlü, ölçeklenebilir ve modüler bir backend framework'üdür. TypeScript ile geliştirilmiş olup, Angular'dan ilham alan bir mimari sunar.

## 2. Proje Klasör Yapısı

```
project-root/
│
├── src/
│   ├── modules/
│   │   ├── users/
│   │   │   ├── dto/
│   │   │   │   ├── create-user.dto.ts
│   │   │   │   └── update-user.dto.ts
│   │   │   ├── entities/
│   │   │   │   └── user.entity.ts
│   │   │   ├── users.controller.ts
│   │   │   ├── users.module.ts
│   │   │   ├── users.service.ts
│   │   │   └── users.repository.ts
│   │   └── auth/
│   │       ├── dto/
│   │       ├── auth.controller.ts
│   │       ├── auth.module.ts
│   │       └── auth.service.ts
│   │
│   ├── common/
│   │   ├── decorators/
│   │   ├── filters/
│   │   ├── guards/
│   │   ├── interceptors/
│   │   └── middlewares/
│   │
│   ├── config/
│   │   ├── database.config.ts
│   │   └── validation.config.ts
│   │
│   ├── app.module.ts
│   └── main.ts
│
├── test/
├── .env
├── nest-cli.json
├── package.json
└── tsconfig.json
```

## 3. Temel Bileşenler Detaylı Açıklama

### 3.1 DTO (Data Transfer Object)

DTOlar, veri transferi için kullanılan sınıflardır. Genellikle input validasyonu için kullanılır.

**Örnek create-user.dto.ts:**
```typescript
import { IsEmail, IsNotEmpty, MinLength } from 'class-validator';

export class CreateUserDto {
  @IsEmail()
  email: string;

  @IsNotEmpty()
  @MinLength(3)
  username: string;

  @IsNotEmpty()
  @MinLength(6)
  password: string;
}
```

### 3.2 Controller

Gelen HTTP isteklerini yöneten ve yanıt dönen sınıflardır.

**Örnek users.controller.ts:**
```typescript
import { Controller, Post, Body, Get, Param } from '@nestjs/common';
import { UsersService } from './users.service';
import { CreateUserDto } from './dto/create-user.dto';

@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Post()
  async create(@Body() createUserDto: CreateUserDto) {
    return this.usersService.create(createUserDto);
  }

  @Get(':id')
  async findOne(@Param('id') id: string) {
    return this.usersService.findOne(id);
  }
}
```

### 3.3 Service

İş mantığını içeren ve veritabanı işlemlerini yöneten sınıflardır.

**Örnek users.service.ts:**
```typescript
import { Injectable, NotFoundException } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { User } from './entities/user.entity';
import { CreateUserDto } from './dto/create-user.dto';

@Injectable()
export class UsersService {
  constructor(
    @InjectRepository(User)
    private usersRepository: Repository<User>,
  ) {}

  async create(createUserDto: CreateUserDto): Promise<User> {
    const user = this.usersRepository.create(createUserDto);
    return this.usersRepository.save(user);
  }

  async findOne(id: string): Promise<User> {
    const user = await this.usersRepository.findOne({ where: { id } });
    if (!user) {
      throw new NotFoundException('Kullanıcı bulunamadı');
    }
    return user;
  }
}
```

### 3.4 Module

Nest.js uygulamasındaki bağımlılıkları ve bileşenleri organize eden sınıflardır.

**Örnek users.module.ts:**
```typescript
import { Module } from '@nestjs/common';
import { TypeOrmModule } from '@nestjs/typeorm';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';
import { User } from './entities/user.entity';

@Module({
  imports: [TypeOrmModule.forFeature([User])],
  controllers: [UsersController],
  providers: [UsersService],
  exports: [UsersService]
})
export class UsersModule {}
```

## 4. Proje Kurulumu

```bash
# Nest.js CLI ile proje oluşturma
npm i -g @nestjs/cli
nest new proje-adi
cd proje-adi

# Gerekli paketleri yükleme
npm install @nestjs/typeorm typeorm postgres class-validator class-transformer
```

## 5. En İyi Pratikler

1. Her modül için ayrı klasör kullanın
2. DTO'ları her zaman kullanın
3. Validasyon için class-validator kullanın
4. Bağımlılık enjeksiyonunu etkin kullanın
5. Hata yakalama ve işleme mekanizmaları geliştirin

## 6. Performans ve Güvenlik İpuçları

- Veritabanı sorgularında index kullanın
- JWT ile authentication
- Rate limiting uygulayın
- Input validasyonuna önem verin
- Hassas bilgileri asla düz metin olarak saklamayın

## 7. Örnek Proje Yapısı İçin Komutlar

```bash
# Yeni bir modül oluşturma
nest generate module users
nest generate controller users
nest generate service users

# Test için
npm run test
npm run test:e2e
```

## Sonuç

Nest.js, modüler yapısı ve TypeScript desteği ile modern backend geliştirmeyi kolaylaştırır. Doğru mimari ve en iyi pratiklerle ölçeklenebilir uygulamalar geliştirebilirsiniz.
