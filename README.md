# Event-Driven Microservices with Python & RabbitMQ / Python ve RabbitMQ ile Olay Odaklı Mikroservisler

---

## English

### Overview
This project demonstrates an event-driven microservices architecture implemented in Python using RabbitMQ as the message broker. Each microservice subscribes to events, processes incoming messages, and emits new events. Docker Compose is used to orchestrate RabbitMQ and all service containers.

### Features
- **Event-driven communication** between services via RabbitMQ  
- **Loose coupling**: services operate independently and communicate through message queues  
- **Scalability**: add more service instances by scaling containers  
- **Dockerized setup** for consistent development and testing environments  

### Architecture
```text
+-------------+    publish     +--------------+
| Service A   |  --------->    |   RabbitMQ   |
| (publisher) |                |   (broker)   |
+-------------+                +--------------+
       ^                              |
       | subscribe                    | deliver
       |                              v
+-------------+              +--------------+
| Service B   | <--------    |  Service C   |
| (consumer)  |    event     |  (consumer)  |
+-------------+              +--------------+
```

### Prerequisites
- Docker  
- Docker Compose  

### Installation & Usage
1. **Clone the repository**  
   ```bash
   git clone https://github.com/your-username/event-driven-microservices.git
   cd event-driven-microservices
   ```
2. **Build and start containers**  
   ```bash
   docker-compose up --build
   ```
3. **Verify services**  
   Open your browser or API client and visit [http://localhost:15672](http://localhost:15672) (RabbitMQ Management UI) with default credentials (`guest` / `guest`). Ensure all microservices are running.
4. **Publish test events**  
   Use provided client scripts or HTTP endpoints to send events and observe inter-service communication via RabbitMQ.

---

## Türkçe

### Genel Bakış
Bu proje, RabbitMQ mesaj aracısı kullanılarak Python ile geliştirilmiş olay odaklı mikroservis mimarisini göstermektedir. Her bir mikroservis olaylara abone olur, gelen mesajları işler ve yeni olaylar yayımlar. Docker Compose ile RabbitMQ ve tüm servis konteynerleri koordine edilir.

### Özellikler
- RabbitMQ üzerinden **olay odaklı iletişim**  
- **Gevşek bağlılık**: servisler bağımsız çalışır, iletişim mesaj kuyruğu ile sağlanır  
- **Ölçeklenebilirlik**: konteyner sayısını artırarak servis örneklerini çoğaltabilirsiniz  
- **Docker ile tutarlı geliştirme ve test ortamı**  

### Mimari
```text
+-------------+    yayınla     +--------------+
| Servis A    |  --------->    |   RabbitMQ   |
| (yayıncı)   |                |   (aracı)    |
+-------------+                +--------------+
       ^                              |
       | abone                       | ilet
       |                              v
+-------------+              +--------------+
| Servis B    | <--------    |  Servis C    |
| (abone)     |    olay      | (tüketici)   |
+-------------+              +--------------+
```

### Gereksinimler
- Docker  
- Docker Compose  

### Kurulum & Kullanım
1. **Depoyu klonlayın**  
   ```bash
   git clone https://github.com/your-username/event-driven-microservices.git
   cd event-driven-microservices
   ```
2. **Konteynerleri oluştur ve başlat**  
   ```bash
   docker-compose up --build
   ```
3. **Servisleri doğrulayın**  
   Tarayıcınızda veya API istemcinizde [http://localhost:15672](http://localhost:15672) adresine gidin (RabbitMQ Yönetim UI) ve varsayılan kullanıcı adı/şifre (`guest` / `guest`) ile giriş yapın. Tüm mikroservislerin çalıştığını kontrol edin.
4. **Test olayları yayınlayın**  
   Sağlanan istemci scriptlerini veya HTTP uç noktalarını kullanarak olay yayınlayın ve RabbitMQ üzerinden servisler arası iletişimi gözlemleyin.

