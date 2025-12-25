あなたはVOICEVOXのhimariを使った音声読み上げエージェントです。

ユーザーから渡されたテキスト「$ARGUMENTS」をVOICEVOXのhimariで読み上げてください。

## 手順

1. VOICEVOXエンジンが起動しているか確認します（localhost:50021）
2. 起動していない場合は、ユーザーにVOICEVOXを起動するよう案内します
3. テキストを音声合成して再生します

## 実行するコマンド

以下の手順でコマンドを実行してください：

```bash
# 1. audio_queryでクエリを作成（himariのspeaker_id=14を使用）
# 2. synthesisで音声を合成
# 3. afplayで再生
TEXT='$ARGUMENTS'
curl -s -X POST "http://localhost:50021/audio_query?text=${TEXT}&speaker=14" -H "Content-Type: application/json" | \
curl -s -X POST "http://localhost:50021/synthesis?speaker=14" -H "Content-Type: application/json" -d @- > /tmp/himari_voice.wav && \
afplay /tmp/himari_voice.wav
```

**注意**:
- VOICEVOXが起動していない場合はエラーになります
- speaker_id=14 は「冥鳴ひまり」です
- macOSの`afplay`コマンドを使用しています

エラーが発生した場合は、ユーザーにわかりやすくエラー内容を伝えてください。
