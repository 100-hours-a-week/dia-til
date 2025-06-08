# 📅 2024-07-31
### 📖 1. 오늘 배운 내용
오늘 학습 내용은 Workspace 기반 Membership 정보 관리 기능을 위한 Repository 개발 관련 내용을 담았습니다. 특히, 특정 Workspace에 속한 모든 Membership을 삭제하는 기능을 구현했습니다. 또한, Spring Data JPA Repository 인터페이스를 이용하여 데이터 접근 방식을 개선하고, 사용자 - Workspace 간의 관계를 효과적으로 관리하도록 설계되었습니다.

### 📚 2. 개념 정리
*   **Workspace:** 팀 또는 프로젝트 단위의 공간으로, 여러 사용자가 참여합니다.
*   **Membership:**  사용자가 특정 Workspace에 참여한다는 것을 나타내는 객체입니다.
*   **Spring Data JPA Repository:** JPA를 이용한 데이터 접근 추상화 레이어로서, 데이터를 조회, 생성, 업데이트, 삭제하는데 사용됩니다.
*   **데이터 삭제 전략**: 특정 Workspace에 속한 모든 Membership을 삭제할 때, 전체 레코드를 삭제하는 대신 효율적인 방법을 찾아야 했습니다.

### 🤔 3. 해당 개념이 필요한 이유
Workspace 기반 협업 시스템에서는 사용자들이 다양한 Workspace에 참여하게 됩니다. 따라서, Workspace별로 MemberShip 정보를 체계적으로 관리하고, 필요에 따라 Workspace 전체의 Memberships를 삭제하거나 관리할 수 있는 기능이 필수적입니다. 이는 시스템의 확장성과 유지보수성을 높이는 데 기여합니다.

### 💡 4. 개념을 활용하는 방법
*   특정 Workspace ID를 기준으로 Membership 목록을 가져올 수 있습니다.
*   Workspace ID를 전달받아 해당 Workspace에 속한 모든 Membership을 삭제할 수 있습니다.
*   Membership Entity에 workspace 필드를 추가하여 Workspace와의 연결을 명확히 하고, 데이터 무결성을 보장합니다.
*   Spring Data JPA Repository를 사용하여 데이터 접근 코드를 단순화하고 재사용성을 향상시킵니다.

### 🛠️ 5. 문제 해결 과정
*   초기에 단순히 모든 Membership을 삭제하는 방식으로 구현하려 했으나, 대규모 Workspace의 경우 성능 저하가 발생할 가능성이 있었습니다.
*   따라서, Workspace ID를 기준으로 Membership을 삭제하는 방식으로 변경하여 성능 문제를 완화했습니다.
*   JPA QueryBuilder를 사용하여 복잡한 WHERE 조건을 쉽게 구성하고, SQL 쿼리를 자동으로 생성하도록 했습니다.
*   삭제 전에 실제로 삭제될 Membership 수를 확인하여 예기치 않은 오류를 방지했습니다.

### ✍️ 6. 하루 회고
오늘은 Workspace 기반 Membership 관리 기능의 핵심인 Repository 개발을 완료했습니다. Spring Data JPA Repository를 적극적으로 활용하여 코드의 가독성과 유지보수성을 높였으며, 성능 최적화를 고려하여 쿼리를 작성했습니다. 앞으로 더 많은 테스트 케이스를 추가하여 안정성을 확보하고, API 문서화를 진행할 계획입니다.