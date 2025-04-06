# astonurt3
깃허브 잔디


class Contact:
    def __init__(self, name, phone_number, email=""):
        self.name = name
        self.phone_number = phone_number
        self.email = email

    def __str__(self):
        return f"이름: {self.name}, 전화번호: {self.phone_number}, 이메일: {self.email}"


class PhoneBook:
    def __init__(self):
        self.contacts = []

    def add_contact(self, contact):
        self.contacts.append(contact)
        print("연락처가 추가되었습니다.")

    def delete_contact(self, name):
        for i, contact in enumerate(self.contacts):
            if contact.name == name:
                del self.contacts[i]
                print("연락처가 삭제되었습니다.")
                return
        print("연락처를 찾을 수 없습니다.")

    def search_contact(self, name):
        for contact in self.contacts:
            if contact.name == name:
                print("연락처를 찾았습니다:")
                print(contact)
                return
        print("연락처를 찾을 수 없습니다.")

    def display_all_contacts(self):
        if not self.contacts:
            print("연락처가 없습니다.")
            return
        print("==== 연락처 목록 ====")
        for contact in self.contacts:
            print(contact)


def main():
    phonebook = PhoneBook()

    while True:
        print("\n1. 연락처 추가")
        print("2. 연락처 삭제")
        print("3. 연락처 검색")
        print("4. 전체 연락처 보기")
        print("5. 종료")
        choice = input("메뉴를 선택하세요: ")

        if choice == "1":
            name = input("이름: ")
            phone_number = input("전화번호: ")
            email = input("이메일(선택): ")
            contact = Contact(name, phone_number, email)
            phonebook.add_contact(contact)

        elif choice == "2":
            name = input("삭제할 이름: ")
            phonebook.delete_contact(name)

        elif choice == "3":
            name = input("검색할 이름: ")
            phonebook.search_contact(name)

        elif choice == "4":
            phonebook.display_all_contacts()

        elif choice == "5":
            print("프로그램을 종료합니다.")
            break

        else:
            print("잘못된 입력입니다. 다시 시도해주세요.")


if __name__ == "__main__":
    main()
