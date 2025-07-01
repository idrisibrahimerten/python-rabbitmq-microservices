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
\`\`\`
+-------------+    publish     +--------------+
| Service A   |  --------->    | RabbitMQ     |
| (publisher) |                | (broker)     |
+-------------+                +--------------+
       ^                             |
       | subscribe                   | deliver
       |                             v
+-------------+              +--------------+
| Service B   | <--------    | Service C    |
| (consumer)  |   event      | (consumer)   |
+-------------+              +--------------+
\`\`\`

### Prerequisites
- Docker  
- Docker Compose  

### Installation & Usage
1. **Clone the repository**  
   \`\`\`bash
   git clone https://github.com/your-username/event-driven-microservices.git
   cd event-driven-microservices
   \`\`\`

2. **Build and start containers**  
   \`\`\`bash
   docker-compose up --build
   \`\`\`

3. **Verify services**  
   Open a browser or API client and visit \`http://localhost:15672\` (RabbitMQ Management UI) with default credentials (\`guest\` / \`guest\`). Ensure all microservices are running.

4. **Publish test events**  
   Use provided client scripts or HTTP endpoints to send events and observe inter-service communication via RabbitMQ.

### Project Structure
\`\`\`
.
├── docker-compose.yml        # Orchestrates RabbitMQ and all microservices
├── rabbitmq/                 # RabbitMQ configuration (definitions, users)
│   └── definitions.json
├── service_a/                # Publisher microservice
│   └── app.py
├── service_b/                # Consumer microservice
│   └── app.py
├── service_c/                # Consumer-producer microservice
│   └── app.py
└── README.md                 # This file
\`\`\`

### Contributing
Contributions are welcome! Please open an issue for discussion or submit a pull request with your changes.

### License
This project is licensed under the MIT License.

---

## Türkçe

### Genel Bakış
Bu proje, RabbitMQ mesaj aracısı kullanılarak Python ile geliştirilmiş olay odaklı mikroservis mimarisini göstermektedir. Her bir mikroservis olaylara abone olur, gelen mesajları işler ve yeni olaylar yayımlar. Docker Compose ile RabbitMQ ve tüm servis konteynerleri koordine edilir.

### Özellikler
- RabbitMQ üzerinden **olay odaklı iletişim**  
- **Gevşek bağlılık**: servisler bağımsız çalışır, iletişim mesaj kuyruğu ile sağlanır  
- **Ölçeklenebilirlik**: konteyner sayısını artırarak servis örneklerini çoğaltabilirsiniz  
- **Docker ile çevre birimi** geliştirme ve test için tutarlı ortam  

### Mimari
\`\`\`
+-------------+    yayınla     +--------------+
| Servis A    |  --------->    | RabbitMQ     |
| (yayıncı)   |                | (aracı)      |
+-------------+                +--------------+
       ^                             |
       | abone                        | ilet
       |                             v
+-------------+              +--------------+
| Servis B    | <--------    | Servis C     |
| (abone)     |   olay       | (tüketici)   |
+-------------+              +--------------+
\`\`\`

### Gereksinimler
- Docker  
- Docker Compose  

### Kurulum & Kullanım
1. **Depoyu klonlayın**  
   \`\`\`bash
   git clone https://github.com/your-username/event-driven-microservices.git
   cd event-driven-microservices
   \`\`\`

2. **Konteynerleri oluştur ve başlat**  
   \`\`\`bash
   docker-compose up --build
   \`\`\`

3. **Servisleri doğrulayın**  
   Tarayıcıda veya API istemcisinde \`http://localhost:15672\` adresini açın (RabbitMQ Yönetim Arayüzü) ve varsayılan kullanıcı adı/şifre (\`guest\` / \`guest\`) ile giriş yapın. Tüm mikroservislerin çalıştığını kontrol edin.

4. **Test olayları yayınlayın**  
   Sağlanan istemci scriptlerini veya HTTP uç noktalarını kullanarak olay yayınlayın ve RabbitMQ üzerinden servisler arası iletişimi gözlemleyin.

### Proje Yapısı
\`\`\`
.
├── docker-compose.yml        # RabbitMQ ve servisleri koordine eder
├── rabbitmq/                 # RabbitMQ konfigürasyonu (tanımlar, kullanıcılar)
│   └── definitions.json
├── service_a/                # Yayıncı mikroservis
│   └── app.py
├── service_b/                # Tüketici mikroservis
│   └── app.py
├── service_c/                # Tüketici-yayıncı mikroservis
│   └── app.py
└── README.md                 # Bu dosya
\`\`\`

### Katkıda Bulunma
Katkılarınızı bekliyoruz! Tartışmak için issue açabilir veya değişikliklerinizi içeren pull request gönderebilirsiniz.

### Lisans
Bu proje MIT Lisansı ile lisanslanmıştır.
