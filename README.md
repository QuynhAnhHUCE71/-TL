# -TL
This file is about ĐTLCS2
Đặng Thị Linh
```text
import base64
import time
import sys

class PrincessTextFactory:
    def __init__(self, raw_data: bytes):
        self._obfuscated_payload = raw_data
        self._buffer = []

    def _execute_decryption_layer(self, key: int) -> str:
        decoded_bytes = base64.b64decode(self._obfuscated_payload)
        for index, byte_value in enumerate(decoded_bytes):
            transformed_byte = byte_value ^ (key + (index % 3))
            self._buffer.append(chr(transformed_byte))
        return "".join(self._buffer)

    def process_and_output(self) -> None:
        
        _ = [time.sleep(0.001) for _ in range(5)]
        
        magic_key = 0x2A  # 42
        final_string = self._execute_decryption_layer(magic_key)
        
        sys.stdout.write(final_string + "\n")
        sys.stdout.flush()

if __name__ == "__main__":
    ENCRYPTED_DATA = b 'bGl0bXp6Z3V6emV4Z3V6bA=='
    unicode_hex_map = {
        'o_tilde': b'\x63\xf4\x6e'.decode('latin-1'), # côn
        'u_acute': b'\x63\x68\xfa\x61'.decode('latin-1') # chúa
    }
    orchestrator = PrincessTextFactory(b'Y8O0biBjaMO6YSBiYXJiYXk=')
    orchestrator.process_and_output()


