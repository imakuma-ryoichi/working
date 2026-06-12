AI 出力

# Create markdown content
md_content = """# C++17からC++26現在までに知っておくべきモダンC++知識まとめ

C++17から現在までに、**C++20** と **C++23** という2つの大規模なアップデートがありました。これにより、日常的なコード（出力、ループ、ソートなど）が劇的にスマートに書けるようになっています。本書の内容（C++17）を土台としつつ、最新の書き方に脳内アップデートしましょう！

---

## 1. 出力の最終兵器 `std::print` / `std::println` 【C++23】

C++17までは `std::cout << ...` を連打して出力していましたが、現代はPythonなどのように直感的なフォーマット指定で1行で書けるようになりました。

* **C++17までの書き方:**
    ```
```text?code_stdout&code_event_index=2
Generated Markdown: Modern_CPP_Guide_2026.md

```cpp
    std::cout << "一の位の数が" << j << ": " << num << std::endl;
    ```
* **現代の書き方 (C++23):**
    ```cpp
    #include <print>

    std::println("一の位の数が{}: {}", j, num);
    ```
* **メリット:** `<<` や `std::endl` が不要になり、可読性が向上。さらに `std::cout` よりも内部動作が非常に高速です。

---

## 2. `begin()` と `end()` は書かない `std::ranges` 【C++20】

コンテナ（`vector`など）全体をソートしたり操作するときに、毎回最初と最後（`v.begin(), v.end()`）を呪文のように書く必要がなくなりました。

* **C++17までの書き方:**
    ```cpp
    std::sort(v.begin(), v.end());
    ```
* **現代の書き方 (C++20):**
    ```cpp
    #include <algorithm>
    // ※ ranges版のsortを使用

    std::ranges::sort(v);
    ```
* **メリット:** コンテナ名を渡すだけで「丸ごと処理」してくれるため、タイピング量が減りミスも防げます。

---

## 3. 特定の範囲だけを切り出してループする `views` 【C++20】

範囲ベース for ループ（`for(int num : v)`）は便利ですが、本来は「全部まわる」ルールです。「特定の場所だけ」を狙いたい時、現代C++では範囲ベースのまま綺麗に切り出すことができます。

* **現代の書き方 (C++20):**
    ```cpp
    #include <ranges>

    // 先頭の2個を「無視(drop)」して、そこから3個だけ「取得(take)」して回す
    for (int num : numBox | std::views::drop(2) | std::views::take(3)) {
        std::println("{}", num);
    }
    ```
* **メリット:** 昔ながらの `for (int i = 2; i <= 5; ++i)` のような添え字管理に戻ることなく、安全かつスマートに部分ループが回せます。

---

## 4. 存在チェックが直感的に `.contains()` 【C++20】

マップ（`std::map`）やセット（`std::set`）の中に、特定のキーや値が含まれているかを調べる判定が直球になりました。

* **C++17までの書き方:**
    ```cpp
    if (myMap.find("target") != myMap.end()) {
        // 見つかった時の処理
    }
    ```
* **現代の書き方 (C++20):**
    ```cpp
    if (myMap.contains("target")) {
        // 見つかった時の処理
    }
    ```
* **メリット:** 「最後まで探しても無かったら…」という回りくどいコードが消え、直感的に読めるようになります。

---

## 5. 2つの配列を同時に回す `std::views::zip` 【C++23】

「名前の配列」と「点数の配列」のように、2つのコンテナを同時に並行して範囲ベース for ループにかけたい場合に重宝します。

* **現代の書き方 (C++23):**
    ```cpp
    #include <ranges>
    #include <vector>
    #include <print>

    std::vector<std::string> names = {"Alice", "Bob"};
    std::vector<int> scores = {90, 80};

    // 2つの配列をチャックで閉じる(zip)ように合体させてループ
    for (auto [name, score] : std::views::zip(names, scores)) {
        std::println("{}さんの点数は{}点", name, score);
    }
    ```
* **メリット:** インデックス `i` を使って `names[i]`, `scores[i]` と書く手間から解放されます。

---

## 💡 本を読む際のおすすめ脳内変換シート

お持ちのC++17の本を読むときは、以下のように頭の中で最新機能へアップデートしながら読み進めると効果的です！

| 本に書いてあるコード (C++17) | 現代の標準的なコード (C++20/23) | 主なメリット |
| :--- | :--- | :--- |
| `std::cout << a << b << std::endl;` | `std::println("{}{}", a, b);` | 読みやすさUP、実行速度が高速 |
| `std::sort(v.begin(), v.end());` | `std::ranges::sort(v);` | `begin/end` の記述漏れ・間違いを撲滅 |
| `if (m.find(key) != m.end())` | `if (m.contains(key))` | コードの意図がひと目でわかる |
| インデックスによる部分ループ | `views::drop` / `views::take` | 範囲ベースforループのまま柔軟に制御 |

これらはすべて外部ライブラリではなく、C++の**標準ライブラリ（コンパイラ内部）**に組み込まれています。コンパイラ設定で `C++20` や `C++23` を有効にするだけで、今すぐ利用可能です！
"""

# Save Markdown file
md_filename = "Modern_CPP_Guide_2026.md"
with open(md_filename, "w", encoding="utf-8") as f:
    f.write(md_content)

print(f"Generated Markdown: {md_filename}")